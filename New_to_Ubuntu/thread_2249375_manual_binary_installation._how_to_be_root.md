---
title: "manual binary installation. how to be root?"
date: 2014-10-21
forum: New to Ubuntu
---

### Post by gnowair on 2014-10-21
hi! thanks for taking the time to pop to this page!

i'd be very grateful to find a way to switch to being root, without having to log out, and back in and so on.

in particular i simply need to drop the binary executable file into usr/bin, but ubuntu isnt letting unless i am root.

thank you very kindly

---

### Post by Iowan on 2014-10-21
You've tried **sudo** or **sudo -i**?

---

### Post by gnowair on 2014-10-21
no, i thought running commands was just for doing things via terminal?
whereas i am trying to learn how to install manually items from download folder.
i will run those commands and see what i see.....
will be back in a minute:::::......

---

### Post by coldcritter64 on 2014-10-21
As noted above put "sudo" (without the quotes) before your move or copy command in a terminal.

```
sudo -i
``` put into a terminal with your password will give you a persistent root terminal to issue commands in, for installing etc, without the need for a graphical root login (NO support can be given for graphical root logins here _ forum rules, due to adherence to Canonical's security model).

**IF** you wish to use nautilus to move/copy files as root _ **TAKE CARE,** you can easily damage your installation with a mistake in a root browser, to get a root browser,
```
gksu nautilus
```
_***SHUT DOWN the browser IMMEDIATELY after doing your root task***_ to minimize potential for catastrophic mistakes very easily being made. Note all the emphasis on the warnings, root browsers and beginners generally don't mix safely.

As per coffeecat's next post read (same link, posted at same time as this post ;))
|
|
V

---

### Post by coffeecat on 2014-10-21
Essential reading:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by gnowair on 2014-10-21
> **Iowan said:**
> You've tried **sudo** or **sudo -i**?

as expected, when i run that command,all it does is ask for NORMAL password,not my ROOT password,and will not help at all for allowing me to copy and paste an item into my usr/bin folder.

the point of my exercise here is MANUAL BINARY INSTALLATION not install via terminal.

thanks anyhow as any efforts by anyone to help is always highly appreciated.

apparently i can log in as root via GUI but as yet i've found no help online as yet. will keep trying,and will check here often in the meantime.

---

### Post by coffeecat on 2014-10-21
> **gnowair said:**
> as expected, when i run that command,all it does is ask for NORMAL password,not my ROOT password,

There is no need to activate the root password. Please read the two posts immediately prior to yours.

---

### Post by coldcritter64 on 2014-10-21
Please read the Rootsudo documentation linked in coffeecat's and my past post.

---

### Post by gnowair on 2014-10-21
> **coffeecat said:**
> Essential reading:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

i am not sure how this would help.

unless i am mistaken, the link there is for doing things via the terminal, whereas i am trying to manully install a binary executable into usr/bin. which i cant do because i need to be root.
and when i attempt by typing any of the above into terminal it will make no difference to the fact that the right-click "paste" option will yet not work, meaning it never made me root exept for what i would tyupe into terminal after it asks for password.
incidently, when i type all above advised commands from either the link above,lor from advice further up the page, i am asked for my normal user password, NOT my root password anyway.

so as yet i still cannot simply paste an item into usr/bin.

---

### Post by gnowair on 2014-10-21
> **coldcritter64 said:**
> Please read the Rootsudo documentation linked in coffeecat's and my past post.


ok, trying again. thank u.

---

### Post by gnowair on 2014-10-21
> **coldcritter64 said:**
> as noted above put "sudo" (without the quotes) before your move or copy command in a terminal.

```
sudo -i
``` put into a terminal with your password will give you a persistent root terminal to issue commands in, for installing etc, without the need for a graphical root login (no support can be given for graphical root logins here _ forum rules, due to adherence to canonical's security model).

**if** you wish to use nautilus to move/copy files as root _ **take care,** you can easily damage your installation with a mistake in a root browser, to get a root browser,
```
gksu nautilus
```
_***shut down the browser immediately after doing your root task***_ to minimize potential for catastrophic mistakes very easily being made. Note all the emphasis on the warnings, root browsers and beginners generally don't mix safely.

As per coffeecat's next post read (same link, posted at same time as this post ;))
|
|
v

PERFECT!
yes, i understand now.

it was the gksu nautilus command that was the part to help me complete the task.

wonderful. although i see the possible dangers of this,for the task i was doing it was pretty dam good.

thanks all for your patience, but as always, i get there in the end.
thanks!

---

### Post by coldcritter64 on 2014-10-21
> ...,all it does is ask for NORMAL password,not my ROOT password

Please,** if** you've enabled your root password use the Rootsudo Documentation to issue the terminal command to lock and delete it. This will bring you back to a more standard installation for help purposes here. It is Ubuntu's security model preferred usage (though ultimately it is up to you how you set up your install).

Open a terminal (CTRL + ALT + T) and copy / paste this next code, enter your _*user*/*sudo *_password and press enter. **Note : **The terminal won't show the password as it is entered.

```
sudo passwd -dl root
``` This will delete the root password set and lock the Ubuntu root account.

Glad to hear the nautilus browser worked for you. Cheers.

---

### Post by gnowair on 2014-10-21
hey.
the account holder here,my self, is the "first created account". HOWEVER, i was still not being abled to paste into usr/bin.

if you read my posting above your last rather rude one, you would see that i had already complted the task at hand.

thank you, SOLVED.

---

### Post by andrew.46 on 2014-10-21
Depending what the executable is you could place the file in* $HOME/bin *. In Ubuntu this is set in your $PATH by $HOME/.profile:

```

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi

```

But this depends on the nature of the executable, if you wish to have other users to have access to it, if you even want executables in $HOME etc. A quick look through my own $HOME/bin shows mostly scripts, youtube-dl, FoxitReader and AtomicParsley. I have had NeroAacEnc, NeroAacTag there before...

---

### Post by Iowan on 2014-10-21
> **gnowair said:**
> 
thank you, SOLVED.Marked it [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") for you ;)

---

### Post by whitesmith on 2014-10-21
This will spare a lot of reading (at the cost of decreasing your Ubuntu knowledge): You can do a "manual binary installation" two ways. From the command line do```
sudo -i
cd /usr/bin
#insert the file by copy or drag-and-drop
``` or from Nautilus do this at the command line```
gksudo nautilus
```This will give a root terminal from which you can do as you please, as coldcritter64 suggested. In keeping with his remarks, operating as root is highly dangerous and can easily lead to irreparable system damage. Close open terminals immediately after using them. Also, Ubuntu disabled the superuser account for security reasons. There is, therefore, no difference between your user password and the sudo password. Please remember that I have given you just enough information to be dangerous. **Do not do anything in either terminal that you fail to thoroughly underfstand!**

---

