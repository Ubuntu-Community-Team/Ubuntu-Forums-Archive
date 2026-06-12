---
title: "Browse &amp; mount shares &gt; webdav or GTK &amp; bash script, please advise"
date: 2007-09-08
forum: Programming Talk
---

### Post by djamu on 2007-09-08
Hi all,

I'm busy building a LiveCD consisting of pxe ( tftpd dhcp.... ) dns nfs proxy server + client.
usage = headless rendernode controller ( included cacti nagios munin monitoring services )
supports LW, Renderman....
a bit like ubuntu studio but purely for number crunching, with headless clients ( custom kernel )
to be made available very shortly.

Here's my problem. 

I need to build a custom GUI either webdav / bash + gtk/xdialog which has network browser functionality ( browsing shares & asingning those to fixed mount points on the boot server so the boot clients can in turn find those shares using the same mount points. 
Users should be able to assign their shares to these mount points in some kind of dialog box.


A webinterface with webdav is my prefered final route, for starters ( as I want to release this real soon ) a bash script + gtk/xdialog or even dialog will suffice.

The problem is that the browsing functionality seems to be quite troublesome as most IDE's ( GLADE & alike ) requires me to program in C. ( I wanted to borrow nautilus-connect-server, or whatever small app. that has browser functionality & can be used with scripts ), but programming something this simpel in C or .. seems  to be totally over the top.

Since this can be done real easy in bash ( except for the browsing ). I'd like some advise on the best approach regarding this.
I've browsed the w3 for some time, but found most solutions either overly complex / not adequate ( nautilus seems not flawless either. )
I looked at jags - smbc - linneighborhood - pyneighborhood - tksmb - xsmbrowser ( the last one until further notice my favorite )

My knowledge of programmig language is limited, - I know how to code microcontrollers in C & ASM :) - but doesn't really apply here.  

Before I start reading details & master a new programming language, thought it might be a good thing to ask the pro's around here. ( this should be a piece of cake ).

Thanks in advance

Jan

---

