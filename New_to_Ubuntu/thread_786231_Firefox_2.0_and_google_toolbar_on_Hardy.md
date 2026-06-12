---
title: "Firefox 2.0 and google toolbar on Hardy"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by jeremymiles on 2008-05-07
Hi Everyone,

I wanted to install the google toolbar (and some add-ons) on Hardy Heron Firefox.  However, that's FF 3, and the add-ons don't work.  So I uninstalled FF 3 and installed FF2. 

When I try to install the add on, it says

"Could not install the file [filename] because: 
Unexpected installation error.  Review the error console log for more details -203".

So I guess the first question is how do I find the error console log?

Thanks,

Jeremy

---

### Post by jeremymiles on 2008-05-08
I think I caused the problem by installing FF2 without doing a complete uninstall of FF3.  

I solved the problem first by doing a complete uninstall in Synaptic, then looking at this thread:


[http://ubuntuforums.org/showthread.php?t=513655](http://ubuntuforums.org/showthread.php?t=513655)

And removing the folders with the extensions and everything else.  Then I rebooted, and reinstalled FF2, and now the toolbar is happy.

Jeremy

---

### Post by sstusick on 2008-05-08
I had this problem too. I just backed up my cookies and bookmarks and then deleted my Firefox profile. After that, it worked fine.

---

### Post by KingTermite on 2008-06-11
> **jeremymiles said:**
> I think I caused the problem by installing FF2 without doing a complete uninstall of FF3.  

I solved the problem first by doing a complete uninstall in Synaptic, then looking at this thread:


[http://ubuntuforums.org/showthread.php?t=513655](http://ubuntuforums.org/showthread.php?t=513655)

And removing the folders with the extensions and everything else.  Then I rebooted, and reinstalled FF2, and now the toolbar is happy.

Jeremy

Thanks...this has been ticking me off for a while now. This did it for me. More work than it "should" have taken, but it does work now. Thanks.

---

### Post by The Populist on 2008-06-11
Can someone walk me through uninstalling Firefox 3? I see the program in Synaptic, but after I uninstall, how do I get Firefox 2?

...

---

### Post by MmmmJoel on 2008-06-11
> **The Populist said:**
> Can someone walk me through uninstalling Firefox 3? I see the program in Synaptic, but after I uninstall, how do I get Firefox 2?

...

To be safe, delete your Firefox profile before installing Firefox 2. Then run:

```
sudo apt-get install firefox-2
```

---

### Post by The Populist on 2008-06-12
Thanks. How do I delete my profile?

...

---

### Post by MmmmJoel on 2008-06-12
> **The Populist said:**
> Thanks. How do I delete my profile?

...
```
rm -r ~/.mozilla/firefox
```

---

### Post by KingTermite on 2008-06-12
> **The Populist said:**
> Can someone walk me through uninstalling Firefox 3? I see the program in Synaptic, but after I uninstall, how do I get Firefox 2?

...

Using Synaptic, mark for deletion FF3 and other FF related tools (search for firefox).

Make sure you back up (export) your bookmarks first, and save your cookies file.

Saving Bookmarks:
Bookmarks->Organize Bookmarks then File->Export

Your cookies file is in:
~/.mozilla/firefox/<some weird profile name>/cookies.txt
Just save that file.

Then delete the entire .mozilla directory from your home directory. This is the key, I think.

Once that is gone, you can go back to synaptic and search for "firefox" again, install firefox 2.

Before installing any other extensions, go and install the google toolbar.

Then installassociated plugins (swf, flash, etc...) if you want from synaptic.

---

### Post by Michael.B on 2008-06-12
You know it might be possible to just edit the extensions installation files and change the max version.  Thought it is easier just to open up about:config and create/set extensions.checkCompatibility to False.

---

### Post by The Populist on 2008-06-12
I appreciate all the help, but I dont know much about directories or configure/extensions. I have messed around with FF3 all day. Some flash pages wont play, and my computer has restarted 3 times today.

Tomorrow I will go with FF2. If I need help getting flash to run in FF2 I'll post here.

Thanks

...

---

