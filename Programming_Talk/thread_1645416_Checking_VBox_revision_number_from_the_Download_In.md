---
title: "Checking VBox revision number from the Download Index"
date: 2010-12-14
forum: Programming Talk
---

### Post by Intrepid Ibex on 2010-12-14
So my little 'task' is to *grep*/*cat*/*sed*/*whatever *the *revision number* of VirtualBox from the Download Index file ([http://download.virtualbox.org/virtualbox/4.0.0_BETA3/](http://download.virtualbox.org/virtualbox/4.0.0_BETA3/)) in order to automate my 'auto-updating' VirtualBox 'packaging script'.

I've gotten to the part where I've wget'd the index file, grepped it to only show one line and now I (somehow) need to get the revision number (68940) out of that line. Of course the version and revision numbers ('*4.0.0BETA3*' and '*68940*') change every time a new version comes up so I'd need something robust for that matter.

So here's the line:
```
<A HREF="Oracle_VM_VirtualBox_Extension_Pack-4.0.0_BETA3-68940.vbox-extpack" NAME="Oracle_VM_VirtualBox_Extension_Pack-4.0.0_BETA3-68940.vbox-extpack"><IMG SRC="/mc-icons/unknown.gif" ALT="[   ]" BORDER=0>  Oracle_VM_VirtualBox_Extension_Pack-4.0.0_BETA3-68940.vbox-extp+</A> 14-Dec-2010 11:07     3M    
```

Thanks for your time,
'Intrepid Ibex' (I hate my nickname but that's all I got)

---

### Post by daqron on 2010-12-17
Is there a particular programming language you're working with here? Here's a perl example (relevant regex in red):
```
if ( $long_string =~ [COLOR="Red"]m/Pack-(.*?)-(.*?)\./[/COLOR] ) {
  print "Version: $1 \n";
  print "Rev: $2 \n";
}
```
That ought to return:
```
Version: 4.0.0_BETA3
Rev: 68940
```
This assumes the naming convention remains consistent, matching everything between "Pack-" and the first hyphen for the version, and everything after the hyphen and before the period for the revision.

---

### Post by Intrepid Ibex on 2010-12-17
Yes, I just wanted to do this with any scripting language (which I told on the first sentence) as long as it gets the job done.

Thanks for the post, however I already managed to do this myself with grep and cut:
```
wget ${_url} -qO - |grep pack |cut -d "v" -f1 |cut -c "51-62"| cut -d "-" -f2
```

---

### Post by Intrepid Ibex on 2010-12-17
[Sigh, double.]

---

