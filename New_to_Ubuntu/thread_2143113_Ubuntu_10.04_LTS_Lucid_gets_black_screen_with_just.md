---
title: "Ubuntu 10.04 LTS Lucid gets black screen with just a white blinking cursor"
date: 2013-05-07
forum: New to Ubuntu
---

### Post by ezpete on 2013-05-07
I am new with Ubuntu but not with computers.

I have an old 32 Bite Lap Top with Win/XP OS, 1 GIG Ram, VIA/S3G Unichrome IGP (Display Adapter), 30 GIG HD
with 7 GIG free space.  

Each time I try do an install of Ubuntu 10.04 LTS Lucid, I select "Try Ubuntu Without Installing" The Set Language screen
appears. English is already selected for me. I hit enter. "Try Ubuntu Without Installing" menu appears again. I hit enter.
I then get a completely black screen with just a white blinking cursor in the upper left corner. Without any intervention on
my part wavy lines appear in the center of the screen. To get out I have to Hit CTR,ALT,DEL.

---

### Post by garvinrick4 on 2013-05-07
Welcome to Ubuntu Forums ezpete. A user with your hardware should be along
in due time.

---

### Post by kostkon on 2013-05-07
> **ezpete said:**
> I am new with Ubuntu but not with computers.

I have an old 32 Bite Lap Top with Win/XP OS, 1 GIG Ram, VIA/S3G Unichrome IGP (Display Adapter), 30 GIG HD
with 7 GIG free space.  

Each time I try do an install of Ubuntu 10.04 LTS Lucid, I select "Try Ubuntu Without Installing" The Set Language screen
appears. English is already selected for me. I hit enter. "Try Ubuntu Without Installing" menu appears again. I hit enter.
I then get a completely black screen with just a white blinking cursor in the upper left corner. Without any intervention on
my part wavy lines appear in the center of the screen. To get out I have to Hit CTR,ALT,DEL.
Support for 10.04 will end in 2 days so I don't see any point in trying to install it right now. Maybe Lubuntu or Xubuntu 12.04 or the latest 13.04 would be more appropriate, although 7GB of space is too low for a normal installation of Ubuntu, regardless of the flavour [i.e. (U)(X)(L)buntu].

Hope that helps.

---

### Post by garvinrick4 on 2013-05-07
Op has a non-pae CPU and would like a Ubuntu install with Gnome2 User interface if at all
Possible as I understand user. I have been away from Ubuntu Forum for a bit and am just
getting back into the last few releases since the default of pae kernel.

---

### Post by garvinrick4 on 2013-05-07
> Support for 10.04 will end in 2 days so I don't see any point in trying  to install it right now. Maybe Lubuntu or Xubuntu 12.04 or the latest  13.04 would be more appropriate, although 7GB of space is too low for a  normal installation of Ubuntu, regardless of the flavour [i.e.  (U)(X)(L)buntu].

Hope that helps.                 
Kostkon
I do believe I remember using Classic Desktop with 11.10 is that still an option for OP.
It does run on his hardware.
EDIT: 11.10 is running short on time also and 12.04 is default pae kernel??? Are there
any viable options for old non pae CPU's?

---

### Post by mörgæs on 2013-05-07
> **garvinrick4 said:**
> Op has a non-pae CPU

What makes you think so?

---

### Post by garvinrick4 on 2013-05-07
> What makes you think so? 				
I should have mentioned that I have talked to OP.
Since I have been away from Ubuntu for a bit I know
little about overcoming installing to non pae CPU's I will
stay out now and let others answer.

---

### Post by mörgæs on 2013-05-07
OK, how does the alternate Xubuntu 12.04.2 work? 

[http://cdimages.ubuntu.com/xubuntu/releases/precise/release/](http://cdimages.ubuntu.com/xubuntu/releases/precise/release/)

Remember to have wired internet access while installing.

---

### Post by mastablasta on 2013-05-08
Lubutnu 12.04 has non PAE image i believe and the OP should be able to boot into live session (alternate installer doesn't have a live session i believe). and 7GB should be enough to install it. but not many additional programmes will fit and also cleaning of old kernel might be needed after updating the OS, because 7GB is a bit low.

furthermore since the 10.04 live session could not be started i suggest usiing some of the available boot options (particulary nomodeset). here is how to do it:  [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by ezpete on 2013-05-08
> **mörgæs said:**
> What makes you think so?

Thank you for your help. I installed Xubuntu 12.04.2 LTS and everything is working fine.

---

### Post by ezpete on 2013-05-08
> **mastablasta said:**
> Lubutnu 12.04 has non PAE image i believe and the OP should be able to boot into live session (alternate installer doesn't have a live session i believe). and 7GB should be enough to install it. but not many additional programmes will fit and also cleaning of old kernel might be needed after updating the OS, because 7GB is a bit low.

furthermore since the 10.04 live session could not be started i suggest usiing some of the available boot options (particulary nomodeset). here is how to do it:  [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Thank you for your help. I installed Xubuntu 12.04.2 LTS and everything is working fine.

---

