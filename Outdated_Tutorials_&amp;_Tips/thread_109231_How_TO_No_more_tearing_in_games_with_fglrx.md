---
title: "How TO: No more tearing in games with fglrx"
date: 2005-12-28
forum: Outdated Tutorials &amp; Tips
---

### Post by BoyOfDestiny on 2005-12-28
Disclaimer: 

Ok you guys, I googled and I think this should work with ati flgrx drivers included in breezy (8.16.20) and higher... I'm using it with 8.20.8 thanks to a how-to here ([http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584))

Now, without further ado, my how-to:

**Proper way:**

Download driconf at [http://dri.freedesktop.org/wiki/DriConf](http://dri.freedesktop.org/wiki/DriConf)

Follow their instructions to extract the archive, then instead of typing python setup.py install, type python driconf

Tnen in the gui check the box next to synchronising the buffer swap with vertical blank. On the right a box with No should appear, click it once to make it Yes.

Reboot (might be uncessary but I'd recommend it)

**Easy way (unverified)**
I assume this works since this is what driconf made... I'd guess this works for you if typing xdriinfo in a prompt returns Screen 0: fglrx.

Make a file in your home dir called .driric

enter this into it

<driconf>
    <device screen="0" driver="fglrx">
        <application name="all">
            <option name="swap_on_vblank" value="true" />
        </application>
    </device>
</driconf>

Save and reboot.

Then that's it, no more tearing in fceu, zsnes, dosbox, mame, with fast scrolling. I've been trying to solve this problem for over a year... (luckily my desktop with a 9200 and open source drivers didn't have this problem, but my dell laptop with x300 had it!)... Anyway, I'm glad ati is embracing DRI, and I hope this works for everyone!
Please reply and let me know if it works for you too!

---

### Post by zi99y on 2006-01-07
Thanks for this, I never heard of it before and my zsnes was a bit "teary" or whatever you call it on my laptop with the ati x700. 

Haven't noticed a huge difference yet, but I'm pretty sure it's better.

I noticed when running the install/compile, that there were a lot of warnings about depreciated files, is this normal/anything to worry about?

And how do I get back to the control panel again?

cheers!

---

