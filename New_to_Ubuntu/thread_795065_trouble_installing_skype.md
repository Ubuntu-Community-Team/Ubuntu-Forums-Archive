---
title: "trouble installing skype"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by furoido on 2008-05-15
I just installed Ubuntu on a barebone pc.

Downloaded skype to my desktop, double-clicked it and got this:
Error: cannot install 'libqt4-gui'

Also tried this:
andrew@andrew-desktop:~$ sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package skype
andrew@andrew-desktop:~$ 

Can anyone help?!
PS I am a COMPLETE AND ABSOLUTE beginner, so please make sure your instructions are really simple and easy-to-understand! Thanks!!

---

### Post by mr-Kirch on 2008-05-15
Just install it off skype.com

---

### Post by mano cazalet on 2008-05-15
another good option is to install it from the [medibuntu]("https://help.ubuntu.com/community/Medibuntu") repos

through synaptic. It will handle the dependencies and also alert you on available updates

---

### Post by furoido on 2008-05-15
__another good option is to install it from the medibuntu repos

through synaptic. It will handle the dependencies and also alert you on available updates


I downloaded the medibuntu repos...how do i access it through synaptic? can't see it listed...

---

### Post by viswanathan on 2008-05-15
dude this documentation would help u surely 

[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

---

### Post by viswanathan on 2008-05-15
> **furoido said:**
> __another good option is to install it from the medibuntu repos

through synaptic. It will handle the dependencies and also alert you on available updates


I downloaded the medibuntu repos...how do i access it through synaptic? can't see it listed...

dude u need to enable medibuntu repos in ur system

---

### Post by mano cazalet on 2008-05-15
do not forget to hit reload, since you added a new repo

or sudo apt-get update
in terminal

---

### Post by furoido on 2008-05-15
Mano,

Obrigadinho para a ajuda, pa! Espero que esta todo bem la no Brazil!!

---

### Post by mano cazalet on 2008-05-15
cheers

I'm glad it worked ;)

***

bem-vindo ao ubuntu amigo
tá ficando friozinho por aqui

---

### Post by btermeli on 2008-05-15
I did it before, download the file from ;

[http://www.skype.com/intl/en/download/skype/linux/choose/](http://www.skype.com/intl/en/download/skype/linux/choose/)

it will be a *.deb file.
open terminal,
write the location of the file if it is on your desktop;

cd Desktop

sudo dpkg -i name_of_the_package_file.deb

After installation, click skype but it wont work but automatic updates will appear. Install updates and click skype again.
and here it goes...

---

### Post by furoido on 2008-05-15
Sorry to disappoint Mano, but didn't work!! tries to install and got this:

skype:
 Depends: libqt4-gui but it is not going to be installed
 Depends: dbus-x11 (>=1.0.0) but it is not installable

---

### Post by mano cazalet on 2008-05-15
:confused:

did u try btermeli's suggestion?

is your hardy 32 or 64 bits?

---

### Post by furoido on 2008-05-15
Think I'm actually running gutsy gibbon (how do I check?!) and no idea if its 32-bit or 64-bit...not sure if its relevant but my pc is an intel Core2 duo E8400...

---

### Post by btermeli on 2008-05-15
go to System >About Ubuntu
which file did u download and install?
Standard personal computer  OR 64bit AMD and Intel computers ?
It should be 64bit if ur pc is core2..

---

### Post by furoido on 2008-05-15
Yep, Says Gutsy Gibbon, But Doesn't Say If 32-bit Or 64-bit...to Be Honest I Downloaded The Program Onto Cd Several Weeks Ago To Try Out On My Old Pc And Can't Remember Which Version...but I Have A Horrible Suspicion It Was The 32-bit Version.

Do I Need To Completely Re-install If I Do Have The Wrong Version, And If I Do, Will I Lose All My Existing Settings, Files, Emails, Etc?

---

### Post by mano cazalet on 2008-05-15
no, the 32bit verion is the one you need

so lets try this command in terminal:

```
sudo apt-get install libaudio2 libqt4-core libqt4-gui
```

---

### Post by furoido on 2008-05-15
andrew@andrew-desktop:~$ sudo apt-get install libaudio2 libqt4-core libqt4-gui
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libaudio2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libaudio2 has no installation candidate

---

### Post by mano cazalet on 2008-05-15
ok, maybe it is not necesssary, try installing skype again, and see what's the output now

---

### Post by furoido on 2008-05-15
if i do a search in synoptic package manager, i get 3 options:

1: skype common. this one seems ok to install
2: skype. this one I get following message:
 Depends: libqt4-gui but it is not going to be installed
 Depends: dbus-x11 (>=1.0.0) but it is not installable
3: Skype-static. This one I get:
Depends: dbus-x11 (>=1.0.0) but it is not installable

If i try to install directly from desktop package I get still get:
cannot intsall 'libqt4-gui'

---

### Post by mano cazalet on 2008-05-15
```
sudo apt-get install libqt4-core libqt4-gui
```

and after this try with skype common

---

### Post by furoido on 2008-05-15
andrew@andrew-desktop:~$ sudo apt-get install libqt4-core libqt4-gui
[sudo] password for andrew:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libqt4-gui: Depends: libaudio2 but it is not installable
E: Broken packages

---

### Post by Rowanmf on 2008-05-15
Guys , sorry to intrude , looking for help with skype as well posted a request for help here :

[http://ubuntuforums.org/showthread.php?p=4963867#post4963867](http://ubuntuforums.org/showthread.php?p=4963867#post4963867)

but have not managed to sort it yet .

Please have a look ...

---

