---
title: "Unable to log out a guest user"
date: 2011-10-05
forum: New to Ubuntu
---

### Post by kimberley on 2011-10-05
I am  unable to log out a guest user and therefore unable to delete him from the system. I used the "unlocked" key and perhaps this is why I now have a blank screen when restarting the computer. Initially on start-up  I have a 256 error message and then after 5 minutes or so I am asked for a password and fortunately am able to log in.  I am using Ubuntu 10.4 which, so far, has given no problems - I love it. 

I have no technical knowledge and if anyone has an answer please, please  keep it simple.:)

---

### Post by ajgreeny on 2011-10-05
Boot to recovery mode from the grub menu, drop to a command line, and then you will be able to remove any user you have made easily with the command ```
userdel *username*
``` and then reboot.

---

### Post by kimberley on 2011-10-06
Thank you for this info. I have to be honest and say that I had to Google grub menu to find out how to carry out your instructions!!

Unfortunately, I got error 27 "unrecognised command" when I entered 'userdel and the user name' on the command line. (Lex' is the user I wish to delete.)

When I shut down the computer Lex's box is ticked as a guest user in addition to my own and it is his I cannot delete.

 I should have mentioned that when the computer restarts I have 3 successive screen messages as follows:
1.  'Could not update ICE authority file/home/lex/.ICE authority'
2. 'There is a problem with the configuration server. (/usr/lib/libconf2-4/gconf-sanity-check2 exited with status 256).
3.'Nautilus could not create the following required folders /home/lex/Desktop,/home/lex/.nautilus'

Is it possible to use a terminal command rather than going to the grub menu?:confused:

---

### Post by Linux_junkie on 2011-10-06
Will this help you in using the command?

---

### Post by maniat1k on 2011-10-06
> **Linux_junkie said:**
> Will this help you in using the command?

I was going to say that! :p

In adition you can try this one

```
deluser –remove-all-files <user>
```

or

```
userdel -r <user>
```

---

### Post by kimberley on 2011-10-07
Thank you for the screen shot which was a great help. I followed this and got the following messages as I tried twice. Unfortunately I cannot paste the screen shots from the clipboard as the 'paste' function is greyed out. 

1.  deluser-remove-all-files: command not found
2.  /usr/sbi/deluser: only root may remove a user or group from the system

The thought of tampering with the root system sounds a bit scary but if it can be spelled out in simple terms I may give it a try with your help.

---

### Post by audiomick on 2011-10-07
> **kimberley said:**
> 
1.  deluser-remove-all-files: command not found

There is a space missing in there. Have a close look at what was posted. Copy and paste is always a good idea.

> 
2.  /usr/sbi/deluser: only root may remove a user or group from the system

  Put a "sudo" in front of it.

```

```
sudo userdel -r <user>

---

### Post by wildmanne39 on 2011-10-07
Hi, the error you are getting is related to a permission issue, here is a link to look at that has the solution but it still requires the recovery mode.
[http://www.google.com/search?client=ubuntu&channel=fs&q=ICE+authority+file%2Fhome%2Flex%2F.ICE+authority%27&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=ICE+authority+file%2Fhome%2Flex%2F.ICE+authority%27&ie=utf-8&oe=utf-8)
Thank you

---

### Post by kimberley on 2011-10-08
Michael,  I did as you suggest and inserted 'sudo' and got the same message, ie ' user del: user lex is currently logged in'

I did also check out the 2 forums mentioned but could not find anything specific or that I understood.
Again, thank you for your suggestions

---

### Post by kimberley on 2011-10-10
I have now partly solved my problem in as much as it is only my password which is asked for when I log in. I disabled 'lex' from automatic log in after a suggestion on a previous forum response.  I can live with logging myself in until April when I shall download the latest version of Ubuntu.

What would I do without this forum!

---

### Post by wildmanne39 on 2011-10-10
Hi, I am glad you have it working again.
Enjoy

---

