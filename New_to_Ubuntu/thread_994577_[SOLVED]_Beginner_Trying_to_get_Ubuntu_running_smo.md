---
title: "[SOLVED] Beginner Trying to get Ubuntu running smoothly"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by rbrsmith on 2008-11-26
Hi to anyone who can help me.  I am trying Ubuntu for the first time and am really keen to get it up and running.  I installed it alright and got the wireless on my laptop running.  The problem is that the entire system runs very slow and choppy, i figure my Nividia graphic card does not have the latest drivers installed, so my problem is how do i install these drivers?  My card is a Nividia GE Force 8200, i went to hardware installer in Ubuntu and tried to install the recommended driver of 177, but nothing happened.  Any help is much appreciated, i have been searching the web looking for assistance but nothing worked.  If someone could guide me through the process or knows what i am doing wrong, that would be awesome.  Thanks

---

### Post by nhasian on 2008-11-26
can we have the specs to your computer?  if your not sure you can run the command

```
lshw -C memory,cpu,display
```

you should be able to install the restricted drivers for your video card by going to *System/Administration/Hardware Drivers*

if you have trouble installing software, try using a different software source by going to *System/administration/software sources* then change the *download from* to *other...* and choose *select best server*

---

### Post by amauk on 2008-11-26
couple of things
1) I've found some new installs are slow for a couple of hours after installation (I think this is the indexer indexing files) after a couple of hours speed is normal - but it's only been noticable on a couple of machines so I've never looked into it

2) Re: restricted drivers, when you say nothing happened did no dialog come up at all?
It should download a file, install it and ask you to reboot (blue icon in the notification area + a balloon info message)

---

### Post by presence1960 on 2008-11-26
This is how I did it, But there are probably other ways to install the drivers. I used Envy NG. go to the link at the end & choose the version of Envy for your Ubuntu version by clicking on Get Envy. Follow the instructions they are really easy. I did this right after my install of Hardy Heron successfully. I was a complete noobi and didn't foul it up so I know you can do this also. [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by eriqjaffe on 2008-11-27
EnvyNG isn't quite as friendly for Intrepid (IIRC, the GTK front-end is broken), but the text interface works fine.

```
sudo apt-get install envyng-core
```

When that's done...

```
sudo envyng -t
```

And just follow the prompts.  That's how I got the nVidia drivers on my desktop after I upgraded to Intrepid.

---

### Post by rbrsmith on 2008-11-27
Thanks alot for your help guys.  I just got it working.  I changed the download source from Main Canada, to Main server and everything went smoothly.  Thanks a lot for your help, the speed of every ones response was amazing.  I'm loving Ubuntu and am looking forward to exploring it over the next few months.  Thanks all.

---

