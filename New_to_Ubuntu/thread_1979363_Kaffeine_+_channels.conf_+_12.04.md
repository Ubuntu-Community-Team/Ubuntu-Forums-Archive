---
title: "Kaffeine + channels.conf + 12.04"
date: 2012-05-13
forum: New to Ubuntu
---

### Post by suomalainen on 2012-05-13
ubunteros,

I have a channel.conf file. When I was using 10.04 I only had to copy this file to .Kaffeine in my home directory and then the channels were automatically set up in Kaffeine.

Now that I use 12.04 I cannot fine .kaffeine in the home directory and even when I did a channel scan with kaffeine and then did a search for channels.conf, believeing kaffeine would have created this file, it was no where to be found.


As I stated, I have a channels.conf file for kaffeine and would like to know to which folder I must copy it to.

Thank you!

---

### Post by suomalainen on 2012-05-14
bump............

---

### Post by suomalainen on 2012-05-16
bump

---

### Post by suomalainen on 2012-05-16
Hello again,

As stated I'm using Ubuntu 12.04 32 bit and Kaffeine 1.2.2.

When I do a channel scan with Kaffeine could somebody please tell me into which folder the generated file is saved in by Kaffeine and what the name of the file I'm looking for is. Thank you!

---

### Post by westie457 on 2012-05-16
Hi suomalainen, I am running Kaffeine in 11.10 there is no channels.conf file here either. The closest I found is scanfile.dvb in the .kde folder.

The real path is /home/user_name/.kde/share/apps/kaffeine

Ended up purging Kaffeine and reinstalling then resetting the channels because the old list did not work for me. I had installed Kaffeine in 10.10 then upgraded to 11.04 was working fine then the upgrade to 11.10 killed Kaffeine for me.

Hope this helps.

---

### Post by suomalainen on 2012-05-16
@ westie457,

Thanks for confirming the folder and path. That was help.

My problem ended up being the fact that I used gksu ""#¤% to copy files over  when I could have simply just drag and drop to home folder.

ANyway deleting then recopying solved my problem!

Thanks

---

### Post by islamux on 2012-08-23
> **suomalainen said:**
> @ westie457,

Thanks for confirming the folder and path. That was help.

My problem ended up being the fact that I used gksu ""#¤% to copy files over  when I could have simply just drag and drop to home folder.

ANyway deleting then recopying solved my problem!

Thanks

 the new place for new version of kaffeine 
/usr/share/kde4/apps/kaffeine/scanfile.dvb

---

