---
title: "Bash: ./inst: No directory found"
date: 2015-12-24
forum: New to Ubuntu
---

### Post by Jacob_Zhang on 2015-12-24
I've been following this tutorial: [www.maketecheasier.com/sync-onedrive-linux/]("http://www.maketecheasier.com/sync-onedrive-linux/") to install Microsoft Onedrive on my laptop.  
On the 4th step, I'm supposed to enter the install script "./inst install". I enter it in and the terminal gives me an error along the lines of  "Bash: ./inst: Directory not found blah blah". I'm pretty sure it's nothing wrong with the file because I've tried a similar tutorial with a completely different file and the same error occurred. 
I retried the tutorial from the beginning at least 5 times and even replaced the "./inst" with "./install", but the error remains. 
A bit of background:
[LIST]
[*]I'm running Lubuntu 32-bit on a Dell lappy with a Pentinum M, 1gb RAM, other ****** specs etc.
[*]Because I have a Pentinum M which doesn't support pae, I had to forcepae on the installation (not sure if this is relevant)
[*]I'm really damn frustrated since this is the third major problem I've come across installing linux.
[/LIST]

Any help would be greatly appreciated. Thanks!

---

### Post by matt_symes on 2015-12-24
Hi

Those instructions are out of date.

Try these commands

```
cd && git clone https://github.com/xybu92/onedrive-d.git 
```

```
cd onedrive-d
```

```
./install.sh
```

```
onedrive-pref
```

Enter your one-drive account details.

Kind regards

---

### Post by sisco311 on 2015-12-24
Welcome to the forums, Jacob_Zhang!

Which version of Lubuntu are you using?

matt_symes is right. The instructions you are following are outdated. 


Whit the `git clone ...' command you have downloaded the source code of the program in the "onedrive-d" directory. In that directory there is a README.md file which contains the installation instructions. If you need any further help with following them, feel free to ask.

---

### Post by Jacob_Zhang on 2015-12-24
Works perfectly. Thanks!

---

