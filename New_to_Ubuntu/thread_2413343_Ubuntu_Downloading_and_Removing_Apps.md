---
title: "Ubuntu Downloading and Removing Apps"
date: 2019-02-24
forum: New to Ubuntu
---

### Post by alejandro202 on 2019-02-24
[FONT=arial]I recently switched to Ubuntu again because I messed up the previous system by downloading software that was not packaged and therefore not available in the sudo apt terminal command. I want become an expert on using the terminal commands to download and remove applications. However the following problem occurred to me:
1. I went to the Ubuntu Software and installed "Atom"
2. I opened Atom and tried it but didn't fully liked it so I wanted to remove it
3. I go to the Installed section of the Ubuntu Software and Atom is not there
4. I go to the Apps Menu and right click the Atom icon (which is also bugged out) and click in Show Details
5. The Ubuntu Software opens but not with the Atom App details, instead it shows the results of "Atom" search in the Ubuntu Software
6. I go ahead and tried to solve this via the terminal, I input << sudo apt list --installed >>, tried to look for the name Atom but it is not displayed
[SIZE=2]7. I go and try << sudo apt remove atom >>, it displays this message: [/SIZE][/FONT]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package atom

[FONT=arial]8. I go to the Ubuntu Software forums with hope that someone kind enough can help me out[/FONT]

---

### Post by deadflowr on 2019-02-24
Ah snap!
I mean I see atom in Ubuntu Software and it's a snap package.
snaps can be removed via snap commands like
```
sudo snap remove atom
```
you can look over all installed snap packages with
```
snap list
```

fwiw it should be uninstallable from Ubuntu Software.
I haven't any idea why it's not showing or removable.
Ubuntu Software issues, huh?
It's can be a temperamental beast...

---

### Post by alejandro202 on 2019-02-24
Thank you, what is the main difference of using sudo apt and sudo snap? I installed Thunderbird Mail through the sudo apt and it doesn't get displayed on the Ubuntu Software Installed menu.

---

### Post by deadflowr on 2019-02-24
> what is the main difference of using sudo apt and sudo snap? 

one deals with apt packages, and the other deals with snap packages.
> I installed Thunderbird Mail through the sudo apt and it doesn't get displayed on the Ubuntu Software Installed menu.
Known bug: [https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/1682455]("https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/1682455")

---

