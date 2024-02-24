import numpy as np 
import pandas as pd
import os
for dirname, _, filenames in os.walk('/kaggle/input'):
    for filename in filenames:
        print(os.path.join(dirname, filename))
/kaggle/input/car-price-predictionused-cars/car data.csv
add Codeadd Markdown
df = pd.read_csv("/kaggle/input/car-price-predictionused-cars/car data.csv")
df.head()
Car_Name	Year	Selling_Price	Present_Price	Driven_kms	Fuel_Type	Selling_type	Transmission	Owner
0	ritz	2014	3.35	5.59	27000	Petrol	Dealer	Manual	0
1	sx4	2013	4.75	9.54	43000	Diesel	Dealer	Manual	0
2	ciaz	2017	7.25	9.85	6900	Petrol	Dealer	Manual	0
3	wagon r	2011	2.85	4.15	5200	Petrol	Dealer	Manual	0
4	swift	2014	4.60	6.87	42450	Diesel	Dealer	Manual	0
add Codeadd Markdown
df.info()
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 301 entries, 0 to 300
Data columns (total 9 columns):
 #   Column         Non-Null Count  Dtype  
---  ------         --------------  -----  
 0   Car_Name       301 non-null    object 
 1   Year           301 non-null    int64  
 2   Selling_Price  301 non-null    float64
 3   Present_Price  301 non-null    float64
 4   Driven_kms     301 non-null    int64  
 5   Fuel_Type      301 non-null    object 
 6   Selling_type   301 non-null    object 
 7   Transmission   301 non-null    object 
 8   Owner          301 non-null    int64  
dtypes: float64(2), int64(3), object(4)
memory usage: 21.3+ KB
add Codeadd Markdown
df.describe()
Year	Selling_Price	Present_Price	Driven_kms	Owner
count	301.000000	301.000000	301.000000	301.000000	301.000000
mean	2013.627907	4.661296	7.628472	36947.205980	0.043189
std	2.891554	5.082812	8.642584	38886.883882	0.247915
min	2003.000000	0.100000	0.320000	500.000000	0.000000
25%	2012.000000	0.900000	1.200000	15000.000000	0.000000
50%	2014.000000	3.600000	6.400000	32000.000000	0.000000
75%	2016.000000	6.000000	9.900000	48767.000000	0.000000
max	2018.000000	35.000000	92.600000	500000.000000	3.000000
add Codeadd Markdown
df['Owner'].value_counts()
Owner
0    290
1     10
3      1
Name: count, dtype: int64
add Codeadd Markdown
df['Car_Name'].value_counts()
Car_Name
city                        26
corolla altis               16
verna                       14
fortuner                    11
brio                        10
                            ..
Honda CB Trigger             1
Yamaha FZ S                  1
Bajaj Pulsar 135 LS          1
Activa 4g                    1
Bajaj Avenger Street 220     1
Name: count, Length: 98, dtype: int64
add Codeadd Markdown
import matplotlib.pyplot as plt
import seaborn as sns
df['Fuel_Type'].value_counts()
Fuel_Type
Petrol    239
Diesel     60
CNG         2
Name: count, dtype: int64
add Codeadd Markdown
sns.countplot(x='Fuel_Type', data=df)
plt.show()

add Codeadd Markdown
df['Selling_type'].value_counts()
Selling_type
Dealer        195
Individual    106
Name: count, dtype: int64
add Codeadd Markdown
sns.countplot(x='Selling_type', data=df)
plt.show()

add Codeadd Markdown
df['Transmission'].value_counts()
Transmission
Manual       261
Automatic     40
Name: count, dtype: int64
add Codeadd Markdown
sns.countplot(x='Transmission', data=df)
plt.show()

add Codeadd Markdown
df.hist(bins=20, figsize=(15, 10))
plt.show()

add Codeadd Markdown
