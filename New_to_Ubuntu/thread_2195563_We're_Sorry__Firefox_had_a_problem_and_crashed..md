---
title: "We're Sorry  Firefox had a problem and crashed."
date: 2013-12-24
forum: New to Ubuntu
---

### Post by gordon33 on 2013-12-24
Hello All


I keep getting a box that starts out as:  "We're Sorry  Firefox had a problem and crashed.  We'll try to restore your tabs and windows when it restarts."  At the bottom of this box is "Quit Firefox" or "Restart Firefox" .  That jazz just started on my HP lap top model G60T-200 running only Ubuntu 10.4.  Every thing worked fine for the last 2 years until yesterday.  Even when connected with a wire to my internet providers modem Firefox crashes.

Before when we clicked on the Firefox icon the lab top would go to [www.yahoo.com](www.yahoo.com).  Now it goes to https.[www.google.com](www.google.com).  When in try to change the address bar or do a search I get that crashed message.  

While I have used the terminal others have provided the code.


MERRY CHRISTMAS TO ALL

Gordon

---

### Post by deadflowr on 2013-12-24
Ubuntu 10.04?
That hit end of life in May.

What firefox version are you running?
Open a terminal and simply run
```
firefox -v
```
my guess would be firefox 20, 6 versions ago.
(It's now at 26, for all supported Ubuntu releases)

You could try making a new firefox profile
Run
```
firefox --profilemanager
```
Then create a new profile and try running it.
(Select and then hit start firefox)
See if that helps.

---

### Post by gordon33 on 2013-12-25
Hello DeadFlowr

I typed in the command and click on Create Profile... Then I typed in a new profile name.  Same problem and command _firefox -v _still shows Firefox 20.

gordon33

---

### Post by deadflowr on 2013-12-25
Was the home page the Ubuntu Start Page, or Google's home page?
The default page on Firefox for Ubuntu looks like Google's home page, but has links for various Ubuntu stuff.
Where as the Google home page is all Google, without any Ubuntu links.
When you make a new profile it will use the Ubuntu start page.

But that may just be beside the point.
The current version you have is old and out of date.
(Both the OS and the browser)

It may be possible, if you're intent on staying on an unsupported OS, to download Firefox directly from 
Firefox.
That's probably the best I can offer on this really.

---

### Post by gordon33 on 2013-12-25
Hello deadflowr

Yes it was google with the Ubuntu links that came up.  Oddly I am sending this from the computer that had the problems.  So it is working now.  I am planing on up dating this lab top with 13.10.  Hope fully 13.10 will have a newer version of Firefox.

Is the system working because i deleted a few files form the Home Folder.  It was not working minutes before deleting a few files and links to some auto repaire forums.

Gordon

---

### Post by deadflowr on 2013-12-25
Any supported version of Ubuntu will have you on the most up-to-date version of firefox-(stable).
I believe that goes for the other flavors as well.(Kubuntu,Xubuntu,Lubuntu,Ubuntu Gnome, etc,etc)

---

### Post by gordon33 on 2013-12-25
Hello Deadflowr

Thank you for all your help.  Its a mystery that this lab top is connecting now.

Gordon

---

