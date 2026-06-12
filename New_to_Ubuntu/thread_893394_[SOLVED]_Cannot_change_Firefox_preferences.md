---
title: "[SOLVED] Cannot change Firefox preferences"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by panorack on 2008-08-18
I've recently upgraded to Firefox 3.0.1 and now I cannot change the default preferences. 

Every time I change them it restores the default settings next time I run Firefox. Very annoying as the settings for Home page, downloads and cookies are not the ones I use. I was able to change them on the previous version so presume this is an issue with this version. Can anyone offer any help with this.


Many thanks in anticipation.

---

### Post by aloshbennett on 2008-08-18
Are you able to close the firefox gracefully? I remember having installed foxmarks plugin, firefox crashes everytime when I try to close it. You could try it once after disabling your plugins.

Also, it might help if you verified the permissions on your profile directory (though I dont see any reason why it should change).

---

### Post by silkstone on 2008-08-18
Things to check...

1. Make sure you don't have another version of FF installed.

2. Is there another instance of FF running? If so, sudo killall firefox

3. Go to ~/.mozilla/firefox and delete profiles.ini

4. If none of that works, delete xxx.default from the same folder, then uninstall and reinstall FF3 from synaptic. (Note that deleting this will lose your bookmarks, so either back them up or use Foxmarks to save them.)

I suspect that remnants of FF2 are probably the main problem, so FF3 is looking in the wrong place for your defaults folder.

---

### Post by panorack on 2008-08-18
> **silkstone said:**
> Things to check...

1. Make sure you don't have another version of FF installed.

2. Is there another instance of FF running? If so, sudo killall firefox

3. Go to ~/.mozilla/firefox and delete profiles.ini

4. If none of that works, delete xxx.default from the same folder, then uninstall and reinstall FF3 from synaptic. (Note that deleting this will lose your bookmarks, so either back them up or use Foxmarks to save them.)

I suspect that remnants of FF2 are probably the main problem, so FF3 is looking in the wrong place for your defaults folder.

Thanks for these suggestions silkstone. Step 3.(deleting the 'profiles.ini' file) solved the problem. Now works OK and changes to the preferences are saved correctly. 

Many thanks for your help.

---

### Post by panorack on 2008-08-19
As a rider, in case this is of any use to anyone else.

1. Deleting the 'profile.ini' file does remove all bookmarks so backup first using 'Organise Bookmarks' option.

2. If like me you have cookies turned off and only allow sites you trust via the 'Exceptions' option you will loose them. I could not find a way of backing-up these so I am having to go through the long process of setting the Exceptions again.

---

### Post by danemaslen on 2009-06-29
I've just encountered this problem and (aided by the suggestions in this thread) managed to find a less drastic solution.

I looked at the contents of ~/.mozilla/firefox/profiles.ini, namely:

[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=h1mxrm6y.default

I then looked at the files in ~/.mozilla/firefox/h1mxrm6y.default and found that prefs.js belonged to root rather than my username.  Once I changed the ownership of prefs.js any modifications I made to my preferences became permanent.

---

