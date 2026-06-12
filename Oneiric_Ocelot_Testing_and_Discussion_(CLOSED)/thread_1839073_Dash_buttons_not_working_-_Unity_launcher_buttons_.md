---
title: "Dash buttons not working - Unity launcher buttons OK."
date: 2011-09-04
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by effenberg0x0 on 2011-09-04
I did a sudo apt-get dist-upgrade && sudo apt-get update && sudo apt-get upgrade && sudo dpkg -configure -a and ran into a new problem.

Now when I am in the dash the buttons "Media Apps", "Internet Apps", "More Apps" and "Find Files" do not work. Nothing happens when I click them. If I insist on clicking any of them a second time, unity crashes. 

The search box also won't work. No matter what I type there, nothing happens.

I am guessing somehow Unity must keep a database of installed apps which is lost or corrupted, or maybe it has no permission to read this. But I can't find it.

Anyone has any tips?

Thanks,
EFfenberg

---

### Post by garvinrick4 on 2011-09-04
Had two installs that were not working also just figured devs still working on dash. Did fresh installs
when beta1 came out and now both are working rather well. Seems to be coming together now. 
This will bump up to front incase user has a fix for you which I know is what you want
I am just giving you my latest clean install report. Have a nice day.

---

### Post by sammiev on 2011-09-04
+1 with the OP.

---

### Post by effenberg0x0 on 2011-09-05
This has fixed the problem for me. 

```
sudo apt-get install --reinstall unity unity-2d unity-2d-launcher unity-2d-places unity-2d-spread  unity-common unity-greeter unity-lens-applications  unity-lens-files  unity-lens-applications unity-lens-music unity-place-applications unity-place-files unity-services

sudo service lightdm restart
```


Regards,
Effenberg

---

### Post by sammiev on 2011-09-05
Hi effenberg0x0, it worked great. Thanks :)

---

