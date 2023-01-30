# Data-Mining-Visualization
import matplotlib as mpl
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import seaborn as sns
sns.set()
import matplotlib.pylab as plt
import plotly.express as px
import seaborn as sns
%matplotlib inline 
from matplotlib import font_manager, rc
import folium
from folium.plugins import MarkerCluster
import json
import geopandas as gpd
from shapely.geometry import Polygon, LineString, Point

font_path = "C:/Windows/Fonts/NGULIM.TTF"
font = font_manager.FontProperties(fname=font_path).get_name()
rc('font', family=font)
//<연도별 범죄 발생 및 검거 건수>
df = pd.read_csv('[범죄(상세죄종)] 연도별 범죄 발생 건수와 검거 건수(2012_) _ 총합 (2021년).csv', encoding='UTF-8' )
df

x = df['날짜']
total = df["발생(건)"]
total2 = df["검거(건)"]

plt.bar(x,total, color = 'b', alpha = 0.35, label='발생')
plt.plot(x,total2, color = 'r', alpha = 0.9, label='검거')

plt.xlabel('연도별')
plt.ylabel('발생(건)')
plt.title('전국 연도별 범죄 발생 및 검거 건수')

plt.xticks(x)
plt.legend()
current_values = plt.gca().get_yticks()
plt.gca().set_yticklabels(['{:.0f}'.format(x) for x in current_values])
