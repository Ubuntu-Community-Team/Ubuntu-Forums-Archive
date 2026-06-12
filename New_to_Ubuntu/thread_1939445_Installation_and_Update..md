---
title: "Installation and Update."
date: 2012-03-11
forum: New to Ubuntu
---

### Post by BreezyCricket on 2012-03-11
I have just installed version 11.1 and would appreciate if someone could tell me how to do software updates.

I believe I had an option in the Ubuntu Software Centre to do this when I first completed the installation but it has disappeared.

Also, I installed a program using the Ubuntu System and would appreciate also if someone could tell me how to find this program. The only option I can find for this is to Remove it, but as to Using it, I guess this is not allowed.

Many Thanks.

---

### Post by grahammechanical on 2012-03-11
Hi

Open the Dash. Click the Ubuntu icon or press the super key.

In the search panel type in the name of the program you installed. The Dash will find it for you. Or you can click on the second of the icons at the bottom of the Dash. That will open the Application lens. Then you can click Installed See xxx more results and scroll down looking for an icon that will remind you of the program.

_Updates_

Open the power cog menu and you should see in the menu something telling you that updates are available or that the OS is up to date. Select that option and Update Manager will load.

Or, open the Dash and type Update Manager in the search panel. Load Update Manager and click Check. You need to be connected to the Internet for this to work. Browse through the list of updates and then click install.

While you have Update Manager open Click Settings. In the Software Sources Dialogue box that opens set how often you want Ubuntu to check for updates in the panel called Automatically Check for Updates. You have the option of Daily, Every two days, Weekly, Every Fortnight, Never.

Regards.

---

### Post by BreezyCricket on 2012-03-11
Thank you for the reply.

Being a REAL expert, I don't know what the Ubuntu Icon is but regardless, I went to the Dash and pushed one of the icons on the bottom of the pop-up window which seemed to lead to the programs and when I typed GVIM, which is what I have been trying to find, it did not find anything.

I then went to the Ubuntu Software Centre and found the installed program manually, but this was in a list of installed items only.

The only option I can see is to 'Remove' it.

---

### Post by UnknownFearNG on 2012-03-11
The Ubuntu Logo is the very first button at the top of the panel. If you click it and then type "gvim" without quotes, you won't find it. At the bottom, you will see four icons. Click the second icon that looks like a ruler, pen, pencil. Then type gvim. It should list it as an "app to download". Here is a screenshot.

---

### Post by BreezyCricket on 2012-03-11
I had already gone through the installation procedure but then could not find the program to use.

I removed it, re-installed it, and had the same problem.

---

### Post by kevdog on 2012-03-12
sudo apt-get update
sudo apt-get upgrade

I'm sorry I don't fully understand your question.  Those two commands that I type at the command line usually do everything I need to.

---

### Post by BreezyCricket on 2012-03-12
Thanks to all for the replies.

I think I must have had a corrupted file, or files, because I did a complete re-installation and everything seems to be working now.

---

### Post by saugatad on 2012-03-12
When your run the update package manager. The software upgrade will automatically be installed with it. You can choose whether to install it or not. You question is a bit confusing..

---

