---
title: "palm centro jpilot setup"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by hubiedo on 2008-06-20
i have had a lot of trouble setting up my palm centro and finally solved the problem. i hope this may help someone else also

here is a great step by step of how to set up your palm:

[http://www.pilot-link.org/README.usb](http://www.pilot-link.org/README.usb)

this will help you to be sure if your usb ports etc are set up right.

i also found that the critical part of the jpilot setup in the preferences on my computer was to try each of the coduits separately once i was sure that the usb connections was right. it always looked like it failed because it starts with the contacts, which i later found out was the only one that wasn't working, and ruined the whole sync and i would get a sync error etc.

my main settings that worked after the usb was working correctly are:

under settings Serial port: usb:
baud rate was 9600

under the address tab i used >= 4.0 since i had a late model palm system-- 
wrong i needed the <= 3.5 (i guess because i had previously set it up from a Tungsten E, not ablsolutely sure about this though, but it finally worked)

under the memo tab i used >=4.0 and it worked.

the other settings are pretty self explanatory, and this is just what i went through to get it all working fine. 

hubie

---

### Post by Mize on 2008-08-01
Now if there was a way to sync to Evolution from Jpilot since gnome-pilot seems to scramble address book fields during sync.

---

