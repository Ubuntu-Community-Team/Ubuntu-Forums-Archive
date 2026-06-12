---
title: "Serial Port Problem in 12.04"
date: 2012-06-05
forum: New to Ubuntu
---

### Post by rogerhph on 2012-06-05
Have upgraded from 11.10 to 12.04.
Serial Port ttyS0 worked fine in 11.10,  ( used in GAMBAS programs) but I cannot open it in 12.04.
Google research shows a permissions problem, so I have tried the following in Terminal :-
 
ls -al /dev/ttyS0 
  and got :-    crw-rw---- 1 root dialout 4, 64    so I then tried :-
 
sudo su
chmod 666 /dev/ttyS0
exit
  and got :-   crw-rw-rw- 1 root dialout 4, 64
 
 
This worked, my GAMBAS serial port programs worked OK as long as computer was left on, but the change did not survive when the computer was shut down & re-started - I was back to  crw-rw---- .........
 
How do I make this change "stick" permanently - or is there a better way to set up my Serial port ?
 
Thanks.

---

### Post by capscrew on 2012-06-05
> **rogerhph said:**
> Have upgraded from 11.10 to 12.04.
Serial Port ttyS0 worked fine in 11.10,  ( used in GAMBAS programs) but I cannot open it in 12.04.
Google research shows a permissions problem, so I have tried the following in Terminal :-
 
ls -al /dev/ttyS0 
  and got :-    crw-[COLOR="Red"]**rw**[/COLOR]---- 1 root **[COLOR="Red"]dialout[/COLOR]** 4, 64    so I then tried :-
 
sudo su
chmod 666 /dev/ttyS0
exit
  and got :-   crw-rw-rw- 1 root dialout 4, 64
 
 
This worked, my GAMBAS serial port programs worked OK as long as computer was left on, but the change did not survive when the computer was shut down & re-started - I was back to  crw-rw---- .........
 
How do I make this change "stick" permanently - or is there a better way to set up my Serial port ?
 
Thanks.

Have you checked to see if you are part of the *dialout* group ( see red in the default settings above)?. You can check with this```
getent group|grep dial
``` I believe if the user is part of that group all will work.

---

### Post by rogerhph on 2012-06-05
Many thanks capscrew - all is better now !
 
```
 
 
for the record I did :-
getent group|grep dial 
and got :- dialout:x:20: which did not have my username at the end of the line
 
then I edited (with gedit) the file /etc/group to add my username 
so the line read :- dialout:x:20:rogerhph and saved the edited file. 
 

``` 
 
Since the world hasn't ended with easy access to serial ports in UBUNTU versions up to 11.10 it seems odd that with 12.04 one has to jump through hoops to get access.
 
Best wishes.

---

### Post by capscrew on 2012-06-05
> **rogerhph said:**
> Many thanks capscrew - all is better now !
 
```
 
 
for the record I did :-
getent group|grep dial 
and got :- dialout:x:20: which did not have my username at the end of the line
 
then I edited (with gedit) the file /etc/group to add my username 
so the line read :- dialout:x:20:rogerhph and saved the edited file. 
 

``` 
 
Since the world hasn't ended with easy access to serial ports in UBUNTU versions up to 11.10 it seems odd that with 12.04 one has to jump through hoops to get access.
 
Best wishes.

Glad we got it right now.  Backwards compatibility is always a problem, and always will be.  All in all this was fairly easy.

---

