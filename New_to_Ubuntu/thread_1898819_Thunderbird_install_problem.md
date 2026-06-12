---
title: "Thunderbird install problem"
date: 2011-12-22
forum: New to Ubuntu
---

### Post by mayavi2011 on 2011-12-22
I have several serious issues when I try to install Thunderbird 3.1.15:-

1) On my machine Thunderbird looks nothing like any of the help file images.
2) Thunderbird wont access my Email account server - 
      after I enter my name, user name and password it only pretends to do anything :sad:
    However I do get authentication errors :eek:
3) I have uninstalled and reinstalled Thunderbird repeatedly, but all to no avail.
4) For reasons best known to itself, now Thunderbird has decided not to  start - I just get that rotating icon for about 30 seconds then it  disappears.
5) All my other net programs work properly web browser, VPN etc.

And last but not least I admit that I am a short tempered newby and getting shorter tempered by the minute :sad:

Anyone got any polite suggestions - I mean apart from an axe?

---

### Post by Frogs Hair on 2011-12-22
Hello and Welcome 

Thunderbird is currently at version 8.0 , so could you please supply some information about your Ubuntu version . If you are running an unsupported version it may be time to update . 

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by Sigma1 on 2011-12-22
Another idea might be to rename, move or delete the files in .thunderbird and / or .mozilla-thunderbird. These hidden files are in your home directory and include all your mail etc. If you haven't used tbird yet, then they won't contain anything you cannot get rid of. They might be interfering with a fresh install though.

---

### Post by BC59 on 2011-12-22
The easier way to install it is through repositories. Open a terminal and paste:

```
sudo add-apt-repository ppa:mozillateam/thunderbird-stable
sudo apt-get update
sudo apt-get install thunderbird
```

That's it

---

### Post by mayavi2011 on 2011-12-25
> **Frogs Hair said:**
> Hello and Welcome 

Thunderbird is currently at version 8.0 , so could you please supply some information about your Ubuntu version . If you are running an unsupported version it may be time to update . 

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)


My system says:-
[COLOR=#000000][FONT=Ubuntu][COLOR=#3C3C3C]You are using Ubuntu 11.04 - the *Natty Narwhal* - released in April 2011 and supported until October 2012.

Does that help?
Thanks
[/COLOR][/FONT][/COLOR]

---

### Post by crazy bird on 2011-12-25
Try installing the latest version, see the post of BC59

---

### Post by mayavi2011 on 2011-12-25
> **BC59 said:**
> The easier way to install it is through repositories. Open a terminal and paste:

```
sudo add-apt-repository ppa:mozillateam/thunderbird-stable
sudo apt-get update
sudo apt-get install thunderbird
```That's it


Unfortunately what I get is the following:-

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 0AB215679C571D1C8325275B9BDB3D89CE49EC21
gpg: requesting key CE49EC21 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

All I can say is Oh Dear :confused:

Any further suggestions?
Thanks

---

### Post by BC59 on 2011-12-25
You have to solve the key problem, run:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0AB215679C571D1C8325275B9BDB3D89CE49EC21
gpg --export --armor 0AB215679C571D1C8325275B9BDB3D89CE49EC21 | sudo apt-key add -
```

---

### Post by mayavi2011 on 2011-12-26
> **BC59 said:**
> You have to solve the key problem, run:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0AB215679C571D1C8325275B9BDB3D89CE49EC21
gpg --export --armor 0AB215679C571D1C8325275B9BDB3D89CE49EC21 | sudo apt-key add -
```


Unfortunately, it didn't make much difference :confused:

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 0AB215679C571D1C8325275B9BDB3D89CE49EC21
gpg: requesting key CE49EC21 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

Obviously my ignorance is not helping :(

There is one other small point: if i try to update ubunto to the latest version; my system insists that there is no update available :(
I don't know whether this gives any clues as to the problem?

---

### Post by BC59 on 2011-12-26
To upgrade to Ubuntu next version run:

```
sudo apt-get install update-manager-core
sudo do-release-upgrade
```

---

### Post by kevincmaker on 2011-12-26
May be it is because of the password problem. What password did you give? Your gmail password?

---

### Post by alphacrucis2 on 2011-12-26
> **mayavi2011 said:**
> Unfortunately, it didn't make much difference :confused:

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 0AB215679C571D1C8325275B9BDB3D89CE49EC21
gpg: requesting key CE49EC21 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

Obviously my ignorance is not helping :(

There is one other small point: if i try to update ubunto to the latest version; my system insists that there is no update available :(
I don't know whether this gives any clues as to the problem?

Maybe the key server was down. Try again later. If all else fails, you can manually copy and paste the text of the ppa key into gedit and save it into a file. You can then import the key from the saved file using synaptic.


Here is the ppa website:

[https://launchpad.net/~mozillateam/+archive/thunderbird-stable]("https://launchpad.net/~mozillateam/+archive/thunderbird-stable")

Click technical details and it will expand that section. Click the link that says Signing Key. Then click the link under KeyID. That will take you to the key text which you can copy and paste as above. You need to copy all the text starting with and including 

-----BEGIN PGP PUBLIC KEY BLOCK-----

and ending and including

-----END PGP PUBLIC KEY BLOCK-----

---

### Post by kevincmaker on 2011-12-26
If there is a username - password problem, then this must surely help :

For some applications including thunderbird, you need to provide an application specific password. For this go to, [https://accounts.google.com/IssuedAuthSubTokens](https://accounts.google.com/IssuedAuthSubTokens) login in to it and type the name of the application whose password you want to generate.

Note that this password is a one time password and you just copy and paste the password and need not remember the password.

Please, let me know whether this works..

---

### Post by mayavi2011 on 2011-12-26
> **BC59 said:**
> To upgrade to Ubuntu next version run:

```
sudo apt-get install update-manager-core
sudo do-release-upgrade
```


UUmmm, what I get are the following messages -

update-manager-core is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded

Checking for a new ubuntu release
No new release found

:confused:

Obviously there is something that I am not doing right :(

---

### Post by mayavi2011 on 2011-12-27
> **mayavi2011 said:**
> UUmmm, what I get are the following messages -

update-manager-core is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded

Checking for a new ubuntu release
No new release found

:confused:

Obviously there is something that I am not doing right :(

After carefully reviewing all the advice I manually loaded the key CE49EC21.
This would appear to have fixed the Thunderbird problem :)
Thanks everyone for the help.

---

