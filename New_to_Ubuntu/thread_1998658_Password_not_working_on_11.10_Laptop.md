---
title: "Password not working on 11.10 Laptop"
date: 2012-06-07
forum: New to Ubuntu
---

### Post by ChrisNZ on 2012-06-07
Old laptop has not been used for a while and then when it was the password didnt work. Tried all of them and still locked out. :mad:

Searched the groups and keep coming up with the [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword) link, however holding down the shift key will not show a standard grub menu for some reason? And if i try to use guest on the login screen it still cannot give me access to passwords till i "Know" what it is! :(

So i used Ctrl+Shift+F4? and got a terminal screen but this will not work using the passwrd (username) command under the name i login under.

Help!

---

### Post by asifnaz on 2012-06-07
Go to recovery mode and type

sudo passwd username

replace username with name you have created 

for example

sudo passwd john

it will ask you to type you new password

---

### Post by SpiderSkull on 2012-06-07
For the grub menu just pressing "arrow up" key works most of the time. (just keep it pressed after bios menu)

---

### Post by robert shearer on 2012-06-07
If it is an older version of Ubuntu then it will be using grub and not grub2 so shift won't work.

iirc you should **hold down the esc key** to get the grub menu.

---

### Post by ChrisNZ on 2012-06-07
> **robert shearer said:**
> If it is an older version of Ubuntu then it will be using grub and not grub2 so shift won't work.

iirc you should **hold down the esc key** to get the grub menu.

Hi Robert and others

Yes that was it - hold (Shift) didnt do it. So I used the (Esc) key on bootup, it then told me a "sticking key" etc so release for a few secconds and then re held (Esc) that did it.
So I then seleceted "Root options" on the new menu and this opens a small area at the bottom of the screen.
Using the command "passwrd username" it gave me the "usual options" for password changing.
However - I then got this "Authentication error manipulation...." so I found here - [http://ubuntuforums.org/showthread.php?t=1772894](http://ubuntuforums.org/showthread.php?t=1772894) some discussion on this and now looking at a fix.

Thanks All - will advise...

---

### Post by ChrisNZ on 2012-06-08
Thanks to Robert and Others here, problem solved.

By hold the Esc key long enough....... it eventually went to the grub menu and 'Recovery' options etc. But by not realising that going in the last menu option - 'start a Root screen'... 
applie the command...
this was bringing up the 'Authorisation error... password not changed'

Go back to the top screen and select 'make mount read and write' or words to that effect, this will mean that the changes you make in the commands like in this case, passwd (username) will be accepted!

And thats put this one to rest! :)

Case closed Sherlocks.

---

