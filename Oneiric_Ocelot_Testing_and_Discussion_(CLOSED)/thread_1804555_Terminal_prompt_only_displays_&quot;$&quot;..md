---
title: "Terminal prompt only displays &quot;$&quot;."
date: 2011-07-14
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by PhantmKllr on 2011-07-14
Not sure if this is a problem but...

I decided that I wasn't happy with my user name (not full name), so I made a new user account (because it seemed too much of a hassle to change my current one.

Now in my brand new user area, I've noticed something a little odd. When running GNOME Terminal, instead of displaying the whole "*username*@*computer-name*:~ $" thing, only the "$" is displayed.

Again, I'm not sure if this is an issue, but it's really buggin' me.

Also, when deleting my old user account, I choose to keep the files. But when I try to access the old user folder, Nautilus states that I don't have the necessary permissions. What commands do I use to change them?

---

### Post by mc4man on 2011-07-14
The state of setting up and using a new/additional user has been broken in one way or another since 11.10 started up or thereabouts.

The one consistent thing has been a terminal with just the $ prompt - last time I tried (the other day),  the terminal was still only semi functional, you could run some commands but not cd to anywhere or forward/backspace in the terminal ect.

To me that's a big enough issue to not bother with at this point.

---

### Post by Toz on 2011-07-14
Looks like by default, a new user is created with the bourne shell as its default shell. How did you create the new account?

To fix this from the command line, open a terminal window and type in:
```
echo $SHELL
```
You will probably see **/bin/sh**

Lets fix this. In the terminal window, type in:
```
sudo usermod -s /bin/bash <userid>
```(where <userid> is your new userid).

You can probably also change this through the Gui front end by searching and changing the Shell entry.

---

### Post by mc4man on 2011-07-14
> **Toz said:**
> Looks like by default, a new user is created with the bourne shell as its default shell. How did you create the new account?

To fix this from the command line, open a terminal window and type in:
```
echo $SHELL
```
You will probably see **/bin/sh**

Lets fix this. In the terminal window, type in:
```
sudo usermod -s /bin/bash <userid>
```(where <userid> is your new userid).

You can probably also change this through the Gui front end by searching and changing the Shell entry.

That seems to be it - set up a new user - 
> echo $SHELL
/bin/sh


---

### Post by PhantmKllr on 2011-07-15
> **Toz said:**
> 
Looks like by default, a new user is created with the bourne shell as its default shell. How did you create the new account?

To fix this from the command line, open a terminal window and type in:
```
echo $SHELL
```
You will probably see **/bin/sh**

Lets fix this. In the terminal window, type in:
```
sudo usermod -s /bin/bash <userid>
```(where <userid> is your new userid)...


I used the new "User Accounts" section in the GNOME System Settings.

Anyway, thanks, this did the trick; I had to use the the username instead of the userid.

I wasn't aware that this had to do with the shell I was using. I'm pretty good with the bash shell, but I'm curious about others, would you recommend another?

---

### Post by Toz on 2011-07-15
Have a look at [http://en.wikipedia.org/wiki/Comparison_of_computer_shells]("http://en.wikipedia.org/wiki/Comparison_of_computer_shells") for a listing of different shells and their features.

---

### Post by PhantmKllr on 2011-07-15
Thanks for all the help, Toz! :D

---

