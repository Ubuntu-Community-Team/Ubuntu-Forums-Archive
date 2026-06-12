---
title: "Overlaying points on Matplotlib collection object"
date: 2011-08-25
forum: Programming Talk
---

### Post by feliscatus on 2011-08-25
Hi All,

I am attempting to plot points (pluses and minuses) over a Matplotlib collection object created by the beachball.py program ([http://obspy.org/browser/obspy/obspy.imaging/trunk/obspy/imaging/beachball.py?rev=1942](http://obspy.org/browser/obspy/obspy.imaging/trunk/obspy/imaging/beachball.py?rev=1942)). 

I am able to plot the points by themselves and the collection by itself, but when I plot the two together the points don't show up even though they are plotted last. What am I doing wrong? My code is below:

```

strike,dip,rake = 150,45,45
x = [-0.75,-0.5,-0.25,0.25,0.5,0.75]
y = [-0.75,-0.5,-0.25,0.25,0.5,0.75]
fig = plt.figure(figsize=(10,10))
ax = fig.gca()
bb_collect = beachball.Beach([strike,dip,rake], linewidth=0.4, facecolor='gray', bgcolor='w', edgecolor='k',alpha=1.0, xy=(0,0), width=2, size=100, nofill=False,zorder=100)
a = ax.add_collection(bb_collect)
ax.autoscale_view(tight=False, scalex=True, scaley=True)
plt.plot(x,y,linewidth=0,marker='+',ms=20,markeredgewidth=3)
plt.xlim(-1,1)
plt.ylim(-1,1)
plt.savefig(evid[nm]+".png")

```Many thanks!

---

