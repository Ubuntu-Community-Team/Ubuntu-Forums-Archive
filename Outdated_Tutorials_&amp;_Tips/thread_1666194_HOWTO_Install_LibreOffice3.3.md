---
title: "HOWTO: Install LibreOffice3.3"
date: 2011-01-13
forum: Outdated Tutorials &amp; Tips
---

### Post by rcayea on 2011-01-13
HOWTO...

Install LibreOffice3.3 In Ubuntu

The following HOWTO should help you install LibreOffice in your Ubuntu or Ubuntu-based
linux machine. As you may be aware, LibreOffice was created based on OpenOffice for various reasons, which is not my purpose to discuss.


1. To begin, start by going to [www.libreoffice.com](www.libreoffice.com) and downloading the .deb package that will be used to install the office suite.

2. Once you arrive at the website follow the following steps, using these pictures as your guide:

3. In the picture below, notice the arrow points at the drop down menu where you are able to choose between 32-bit or a 64-bit architecture install.


4. You will notice in the next picture that the red arrow is pointing specifically at the .deb installer file, as opposed to the language pack. We want the installer file.
Click on the installer and take note of where it is downloading to.

5. The next picture simply shows what the package should look like once downloaded.

6. The next picture shows the options available once you right-click directly on the package you just downloaded.Right-click on the package and select, "Extract Here". 
NOTE: If you do not have the "Extract Here" option you may install it by typing the following without the quotes into a terminal(access a terminal in Ubuntu with, ctrl+alt and t: "sudo apt-get install nautilus-open-terminal".

7. Once extracted you will want to look for a folder named similar to the package you just extracted - in this case, LibO_3.3.0...

8. Open the folder. Once you have done this, you should see a folder named, DEBS, just like
the picture below. Click on this folder. You will now be in the DEBS directory.

9. Right click anywhere in the whitespace and you should see the Open-In-Terminal option as seen in the picture directly above. Select it and a terminal window will open.
If you don't see "Open-In-Terminal" this simply means you don't have it installed.

10. To install it, run this command in your terminal window
without the quotes: "sudo apt-get install nautilus-open-terminal".

11. You will have to log out and log back in and then continue this tutorial.

12. Now that your terminal window shows you being in the DEBS directory, all you have to do is run a command to start the installation process.


13. The command to run, as shown in the picture below, is: sudo dpkg -i *.deb

"sudo" = super user privileges, "dpkg" = debian package system, "-i" tells dpkg to install
"*"= means any of the following, and ".deb" is the file type dpkg is looking for.

14. Your next task is to change into the desktop-integration folder and run the same sudo dpkg -i *.deb command again.

15. This picture below shows what you should have written in your terminal if you have successfully changed into the desktop-integration directory(folder).

16. Now simply type the command again: sudo dpkg -i *.deb

17. Once you see all the words fly by your eyes in the terminal and all is finished, you should be able to go to, Applications -> Office and select one of the LibreOfficevtools to use.

If you have any questions, comments, or suggestions, please email me at [email]admin@tuxandpucks.com[/email]

---

