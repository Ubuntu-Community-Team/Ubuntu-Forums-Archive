---
title: "customizing axis lables of two images using imshow"
date: 2013-03-10
forum: Programming Talk
---

### Post by abraxas334 on 2013-03-10
Hi,
I want to draw 2-d histograms using imshow() with matplotlib. I managed to do this with the following code and the image generated is the one I am interested in and I have attached.

[PHP]
#imports
import numpy as np
import matplotlib.pyplot as plt
import matplotlib.cm

#filenames
filename =  'file1.dat' #two columns first with data in range of 10 and 55 and second in range of data between 0.8 and 4
filename1 = 'file2.dat'

#loading data into variables 
data = np.loadtxt(filename)
data1 = np.loadtxt(filename1)

x = data[3414:,0]
y = data[3414:,1]

x1 = data1[:,0]
y1 = data1[:,1]


# Estimate the 2D histogram
#limits for the histogram
min_x = 10
max_x = 55
min_y = 0.8
max_y = 4.0
#calculating the histogram
H, xedges, yedges = np.histogram2d(x, y, range=[[min_x,max_x], [min_y,max_y]], bins=(90, 64) )
H1, xedges1, yedges1 = np.histogram2d(x1, y1, range=[[min_x,max_x], [min_y,max_y]], bins=(90, 64) )


# Histogram needs to be flipped and rotated
H = np.rot90(H)
#H = np.flipud(H)
H1 = np.rot90(H1)
#H1 = np.flipud(H1)

# Mask zeros
Hmasked = np.ma.masked_where(H==0,H) # Mask pixels with a value of zero
Hmasked1 = np.ma.masked_where(H1==0,H1) # Mask pixels with a value of zero



# Plot 2D histogram using pcolor
fig = plt.figure()
ax = fig.add_subplot(111)

cmap = matplotlib.cm.binary
cmap1 = matplotlib.cm.Reds
yedges=yedges*0.01
yedges1=yedges1*0.01


plt.imshow(Hmasked, cmap=cmap, vmin = -10, vmax =40, extent = [0,0.7,0,1.3])
plt.imshow(Hmasked1, cmap =cmap1,vmin =-10,  vmax =40, extent = [0,0.7,0,1.3])


cbar = plt.colorbar()
#ticklables

matplotlib.pyplot.show()

[/PHP]

Now if i plot this, the axis lables for the image are are not the ones I need. I would like to be able to specify the tick lables and tickpoints in such a way:
[PHP]
xtick_locks = [10,30,50,70]
xtick_labl =  [int(xedges[10]), int(xedges[30]), int(xedges[50]), int(xedges[70])]
ytick_locks = [60,40,20,0]
ytick_labl =  [yedges[4], yedges[24],  yedges[44],  yedges[64] ]
plt.xticks(xtick_locks,xtick_labl, fontsize = 30)
plt.yticks(ytick_locks,ytick_labl, fontsize = 30)
[/PHP]
However if I try and add this, I end up with an empty plot, but the right axis labels.  
How can I keep my two superimposed images and the right ticklabels and locks? I clearly do not quite understand how to handle the plot environment yet. 

This is the image with the correct tick lables but not the 2dimage displayed.

Thanks for any help!

---

