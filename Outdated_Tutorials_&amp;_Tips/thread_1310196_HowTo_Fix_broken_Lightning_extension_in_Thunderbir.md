---
title: "HowTo: Fix broken Lightning extension in Thunderbird on karmic koala 9.10"
date: 2009-11-01
forum: Outdated Tutorials &amp; Tips
---

### Post by morfeasrev on 2009-11-01
After upgrading to karmic 9.10 my Lightning extension in Thunderbird stopped working.
The method described on thread [http://ubuntuforums.org/showthread.php?t=1145351](http://ubuntuforums.org/showthread.php?t=1145351) (a howto solving the same problem on 9.04) is not applicable on karmic 9.10 since libstdc++5 is not available through synaptic any more.

So I`m starting this howto explaining what worked for me.

First remove Lightning from Thunderbird: Tools->Addons, select Lightning, and uninstall and then close Thunderbird. 
Don`t be afraid, since this will not erase your appointments.

Then install lightning-extension through synaptic or by just typing in a terminal:
```
sudo apt-get install lightning-extension
```
Thats all you have to do. Now run thunderbird and watch it using lightning:)
The extension in the repos is currently up to date.

Note 1: This is a universe package so you might have to enable them through system -> administration -> software sources.
Note 2: You might want (or not) install the package calendar-google-provider witch is suggested by lightning-extension

---

### Post by kolinab on 2009-11-05
THANK YOU!!

I don't use my lightning every day and was very distressed this afternoon to see that not only was all my data missing, but I could not make new events or anything. 

Does anyone know what the problem is here? I recently did a fresh install of Karmic, (preserving my /home partition as always). All my mail and other firefox/thunderbird data seemed to migrate seamlessly.

Secondly, can someone tell me what the filename(s) are of my lightning data are?

Cheers for this solution. Uninstalling the extension and reinstalling the version from the mozilla website didn't fix the problem but this did.

K

---

### Post by louBurnard on 2009-11-07
Thanks for pointing this out -- I found that actually I needed to 

```
sudo apt-get remove lightning-extension 
```

as well as deactivating it within thunderbird -- but once I'd done that and reinstalled, phew my calendar came back, so now I know what I should be doing today ;)

---

### Post by KarenAK on 2009-12-31
@morfeasrev

worked like a charm ! THANK YOU :-)

---

