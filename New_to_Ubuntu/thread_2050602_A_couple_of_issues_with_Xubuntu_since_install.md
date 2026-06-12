---
title: "A couple of issues with Xubuntu since install"
date: 2012-08-31
forum: New to Ubuntu
---

### Post by newparrot on 2012-08-31
Hello  Sorry to be posting AGAIN lol  Just have a couple of issues I cant seem to find the solution to-  Number 1- I cant play DVDs/cds on the laptop. I tried altering permissions and it isnt this-is it something to do with a driver I need? I post this regarding graphics card   adrian@adrian-TravelMate-2200:~$ lspci | grep VGA 01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]   and the second issue is Firefox-for some reason drop down boxes do not work in anyway shape or form on webpages-I tried unticking the box in settings for using hardware acceleration where available but this hasnt worked.  Could you help me please?

---

### Post by newparrot on 2012-08-31
Sorry for the cheeky bump but still struggling with these issues :(

---

### Post by Rodney9 on 2012-08-31
Playing DVD's - [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by Autodave on 2012-08-31
> **newparrot said:**
> Sorry for the cheeky bump but still struggling with these issues :(

[http://ubuntuforums.org/showthread.php?t=766683&highlight=flash+quit+youtube](http://ubuntuforums.org/showthread.php?t=766683&highlight=flash+quit+youtube)

Go there abd do what it says: your DVDs should play then.

I did NOT write this!  However, I have used it probably 30 or 40 times with success each time.

Goos luck!

---

### Post by newparrot on 2012-09-01
Hi

I have done the first link and the DVD is spinning in the drive but not playing.

The second link throws up error code in terminal when using the sudo commands

Changed browser from FF to chromium and still experiencing issues with drop down menus also

Thanks for all the help so far

---

### Post by newparrot on 2012-09-01
Also, I cannot click on tabs when I open up a window in settings for example on permissions, it just flicks straight back to the original tab. Also the way the mouse deals with scroll downs is bizarre.

Generally im not totally useless with computers, I am getting really disheartened with Linux, regret wiping XP now, for all its faults at least I could use it :(

---

### Post by Autodave on 2012-09-01
> **newparrot said:**
> Hi

I have done the first link and the DVD is spinning in the drive but not playing.

The second link throws up error code in terminal when using the sudo commands

Changed browser from FF to chromium and still experiencing issues with drop down menus also

Thanks for all the help so far

If you are getting the "ruby ripper" not found, paste the command into the window, and then using the left arrow key, go back and delete "ruby ripper" from the command line.  Now, use right arrow key and go back to end of command and execute.

---

### Post by newparrot on 2012-09-01
When I do the first command autodave i get this




adrian@adrian-TravelMate-2200:~$ sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo sed -i "/^# deb .*partner/ s/^# //" /etc/apt/sources.list && sudo apt-get --quiet update && sudo apt-get -y --force-yes --quiet --allow-unauthenticated install medibuntu-keyring app-install-data-medibuntu apport-hooks-medibuntu && sudo apt-get update
[sudo] password for adrian: 
--2012-09-01 16:40:04--  [http://www.medibuntu.org/sources.list.d/maverick.list](http://www.medibuntu.org/sources.list.d/maverick.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 88.191.127.22
Connecting to [www.medibuntu.org|88.191.127.22|:80](www.medibuntu.org|88.191.127.22|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
2012-09-01 16:40:05 ERROR 404: Not Found.

adrian@adrian-TravelMate-2200:~$

---

### Post by gandaran on 2012-09-01
> **newparrot said:**
> When I do the first command autodave i get this




adrian@adrian-TravelMate-2200:~$ sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo sed -i "/^# deb .*partner/ s/^# //" /etc/apt/sources.list && sudo apt-get --quiet update && sudo apt-get -y --force-yes --quiet --allow-unauthenticated install medibuntu-keyring app-install-data-medibuntu apport-hooks-medibuntu && sudo apt-get update
[sudo] password for adrian: 
--2012-09-01 16:40:04--  [http://www.medibuntu.org/sources.list.d/maverick.list](http://www.medibuntu.org/sources.list.d/maverick.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 88.191.127.22
Connecting to [www.medibuntu.org|88.191.127.22|:80](www.medibuntu.org|88.191.127.22|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
2012-09-01 16:40:05 ERROR 404: Not Found.

adrian@adrian-TravelMate-2200:~$
medibuntu website could be down for the moment, try again tomorrow or maverick is no longer supported then you will have to upgrade to 12.04.

edit:
maybe your code is wrong, try this one
```
sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
[http://www.medibuntu.org/repository.php](http://www.medibuntu.org/repository.php)

---

### Post by Autodave on 2012-09-01
> **gandaran said:**
> medibuntu website could be down for the moment, try again tomorrow or maverick is no longer supported then you will have to upgrade to 12.04.


I just used that last week and it was fine: everything upgraded next time UPDATE MANAGER ran.

---

### Post by Autodave on 2012-09-01
> **Autodave said:**
> I just used that last week and it was fine: everything upgraded next time UPDATE MANAGER ran.

You might have gotten a bad download or bad burn of the .iso file.  Also, I would definately use the "alternative" installation .iso.  If you didn't use the alternative one, I would suggest that first.

Reinstall using alternative .iso.
After install, install all updates (probably around 300 of them now)
Go back to my previous post and install the medibuntu repository and everything else in that post. (refer to the elimination of the "ruby ripper" part of command line.
Reboot and install all updates.
From terminal run, sudo apt-get update
From terminal run sudo apt-get upgrade
Reboot.

Let us know what happens.

---

### Post by newparrot on 2012-09-01
THe alternative code throws up the exact same error but thanks anyway

Do you mean re install xubuntu? This will be the third time now :(

Is there a Linux OS that is more user friendly and less difficult to get going? 

I was looking forward to trying it out but I am getting very fed up with everything :(

---

### Post by gandaran on 2012-09-01
> **newparrot said:**
> THe alternative code throws up the exact same error but thanks anyway

Do you mean re install xubuntu? This will be the third time now :(

Is there a Linux OS that is more user friendly and less difficult to get going? 

I was looking forward to trying it out but I am getting very fed up with everything :(
you can still get and install all needed packages (like [COLOR="Red"]libdvdcss2[/COLOR] for dvd playing) from medibuntu by downloading the .deb packages.
[http://packages.medibuntu.org/maverick/index.html](http://packages.medibuntu.org/maverick/index.html)
[http://packages.medibuntu.org/maverick/libdvdcss2.html](http://packages.medibuntu.org/maverick/libdvdcss2.html)
not sure why the right code didn't work as you can access the medibuntu packages directly so the website is up!

edit:
you actually have maverick 10.10 or some other version?

---

### Post by newparrot on 2012-09-01
when I try and install the repositories(or access them using the command given anyway) (link on medibuntu) I get the same error message 404.

I dont know what Maverick is, I installed xubuntu 10.0 and then did a partial upgrade to 11.4-it would not allow a full upgrade and my machine cannot cope with 12.4.(tried and failed)

---

### Post by gandaran on 2012-09-01
> **newparrot said:**
> when I try and install the repositories(or access them using the command given anyway) (link on medibuntu) I get the same error message 404.

I dont know what Maverick is, I installed xubuntu 10.0 and then did a partial upgrade to 11.4-it would not allow a full upgrade and my machine cannot cope with 12.4.(tried and failed)
so maybe your system is broken and is the problem, try installing 11.04 instead of upgrade or I would recommend trying Lubuntu 12.04, Lubuntu is lighter than Xubuntu, try it using the live session then if it works on your machine install it
[http://lubuntu.net/](http://lubuntu.net/)

---

