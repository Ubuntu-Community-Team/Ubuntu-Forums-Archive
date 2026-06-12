---
title: "Copy files from hard drive"
date: 2016-08-01
forum: New to Ubuntu
---

### Post by lookup6236 on 2016-08-01
Hello. I am new to Ubuntu so I'm posting in this forum. If my situation doesn't fit here, please redirect me.

A friend has asked me to try and retrieve a Joomla website that he has on an HP Proliant ML110 G6 running Ubuntu 11.04. He has been using it as a intranet server in a small office environment. Recently the server hasn't been accessible on the network. When I try to access the server directly, all I get is a flash of a black screen with white writing, then dumped back to the login screen. I have downloaded a 11.04 disk and have booted to it, clicking "Try Ubuntu". It appears that I can access the hard drive, but not being familiar with the file structure, I'm not sure where to look. The files I need to find and retrieve are: The folder in which the Joomla site resides, (was accessed from a web browser via 20.20.20.333/internalweb), and the MYSql database that runs it.

Any help in pointing me in the right direction would be very much appreciated!

---

### Post by Bucky Ball on 2016-08-01
Welcome. Firstly, forget trying this with 11.04. It is ancient and hasn't been supported in years, which is possibly why the user started having these issues in the first place. Definitely not the place to be with an office/production setup, particularly one that is supposedly secure. Production environments should stick with LTS releases which have five years support. 11.04 wasn't one of those. Interim releases now have nine months support (was eighteen at one time) so pointless for a production environment.

I'd download regular 16.04 LTS desktop ISO, create bootable media, boot from it *on the server machine*, select 'Try Ubuntu' from the options screen, copy the files you want from the server hard drive to an external drive.

Now you have a backup. Do a clean install of 16.04 LTS server (if that's what's required) to the server and reconfigure to your liking.

---

### Post by lookup6236 on 2016-08-01
Thanks for the quick reply. My problem is I'm not familiar enough with the file structure to find the folder and database that I need to copy. When using Ubuntu as a local server, would the files for the website, (the files I need to copy), be loaded in a specific folder by default? Or is that up to the person setting up the server?

Thanks again!

---

### Post by Bucky Ball on 2016-08-01
The owner doesn't know where things are? They don't know where their Joomla install resides on the hard drive? Perhaps you better sit them down with a piece of paper and see what they can recall. Or boot to 'Try Ubuntu' (a 'live' session) and have a look around. Tell us what you've got. 

Knowing where the administrator has put things or how they've set this up is impossible from this end and any suggestions would be guesswork. See what you can find out from the source and we may be able to scramble further on the strength of that knowledge ... ;)

---

### Post by Geoffrey_Arndt on 2016-08-02
Using search from the nautilus files manager, the Joomla files should be in both /var and /opt.    Typically .. 
/var/www/joomla/installation/

---

