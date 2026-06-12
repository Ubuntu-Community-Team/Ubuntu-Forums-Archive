---
title: "XP to *buntu migration tips"
date: 2009-12-27
forum: Outdated Tutorials &amp; Tips
---

### Post by Kver on 2009-12-27
This is a small collection of mostly random "gotchas" I encountered when migrating other people to *buntu for various reasons. Most of these assume WUBI will not be used to run *buntu at full speed.

I do not take responsibility if your computer dies as a result of my ineptitude. But should it fry, please post! I'll correct tips.

Covers...
[LIST]
[*]Moving Outlook Accounts on XP to Thunderbird/Kmail/etc on *buntu
[*]Migrating bookmarks from XP to FireFox *buntu
[*]Setting up Ubuntu Software Centre/Center on !Ubuntu
[*]Playing Encrypted DVDs
[*]Getting sound working (should all else fail)
[/LIST]

[SIZE="3"]**Moving Outlook Accounts on XP to Thunderbird/Kmail/etc on *buntu**[/SIZE]
[COLOR="#AAA"][SIZE="1"]Use this for a perfect account-migration from XP to Ubuntu. You might be required to re-enter a users mail password for most programs, otherwise, all their messages/accounts/mailbox settings will be migrated.[/SIZE][/COLOR]

[LIST=1]
[*]Install Thunderbird on XP
[*]Use the ThunderBird to import the Outlook profiles.
[COLOR="#AAA"][SIZE="1"]Thunderbird and most open-source mail applications use or recognise a standard arrangement of folder/files, importing to Thunderbird sets this up for you.[/SIZE][/COLOR]
[*]Copy all the files in *%AppData%\Thunderbird\Profiles\xxxxxxxx.default\*
[COLOR="#AAA"][SIZE="1"]Where %AppData% can be found by typing %AppData% into the windows command-line. Usually AppData can be found in the desired users "Documents and Settings" folder, then "Application Data" or "Roaming" folders. xxxxxxxxx is a string of random characters.[/SIZE][/COLOR]
[*] Paste these files into a removable drive, or somewhere you can find when you reboot into *buntu. Additionally, if you can find this folder in *buntu, then you don't need to copy it, just open it in *buntu.
[*] Install Thunderbird in *buntu if not already installed.
[*] Find the ~/.thunderbird/xxxxxxxx.default/ folder.
[COLOR="#AAA"][SIZE="1"]Where ~ is your own home folder, most file-managers such as Dolphin or Nautilus have dedicated home buttons. You might need to find the setting to show hidden files, as .thunderbird is hidden. You may also type it into the navigation bar. xxxxxxxxx is again, random characters.[/SIZE][/COLOR]
[*] Copy the folder, and paste it in the same folder, name the new folder xxxxxxxx.default.bk
[COLOR="#AAA"][SIZE="1"]This is just a backup folder, in case anything goes horribly wrong, just delete xxxxxxx.default and then remove the ".bk" from the folder you just made if things don't work.[/SIZE][/COLOR]
[*] Find the previous files you copied/located. Copy everything from the original xxxxxxx.default folder into the new xxxxxxx.default folder, if asked, overwrite everything.
[*] Open Thunderbird, it should now have all your messages and account settings! You might be asked for your mail password when you first open Thunderbird.
[*] If you prefer other programs, open the program you prefer to use, and find the import features to import your account settings (very much like we imported the outlook account into thunderbird); importing to Kmail is under the "Import Messages" option[/LIST]


[SIZE="3"]**Migrating bookmarks from XP to FireFox *buntu**[/SIZE]
[COLOR="#AAA"][SIZE="1"]There are 3 methods to get your bookmarks, if you already have firefox on Windows, if you do not, and if you want to use Xmarks.[/SIZE][/COLOR]

No Firefox on XP
[LIST=1]
[*]Install Firefox on XP
[*]Use Firefox to import bookmarks, it might do this on first run.
[/LIST]

Via Xmarks
[COLOR="#AAA"][SIZE="1"]Xmarks is a convenient way to synchronise bookmrks and setting across multiple firefox installations. While very convenient, it will embed itself into some pages such as Google (this can be disabled), and requires an account. Also, if privacy is a concern, I don't recommend Xmarks, as your information will be uploaded to Xmarks servers. There is no cost to use Xmarks.[/SIZE][/COLOR]
[LIST=1]
[*](on XP) from Firefox, install the Xmarks addon
[*]Restart firefox, Xmarks will pop up. Follow the prompts to set up Xmarks. Ensure you sync your bookmarks to the server.
[*](on Ubuntu) from Firefox, install the Xmarks addon
[*]Restart firefox, Xmarks will pop up. Follow the prompts to set up Xmarks. Ensure you sync your bookmarks FROM the server, and delete the bookmarks on the computer.
[/LIST]


[SIZE="3"]**Setting up Ubuntu Software Centre/Center on !Ubuntu**[/SIZE]
[COLOR="#AAA"][SIZE="1"]Ubuntu software-centre/center is the successor to various tools used to manage repositories and programs. On Ubuntu this program comes standard, however it is a must-have for other distros aswell should it be for new users. Power-users can more quickly use the Terminal.[/SIZE][/COLOR]

[LIST=1]
[*] Open a Terminal Application
[COLOR="#AAA"][SIZE="1"]Under Kubuntu it's found in Applications>System>Terminal[/SIZE][/COLOR]
[*] enter ```
sudo apt-get install software-store
```
[*] Type your password if requested.
[*] It is now under Applications>System>Software Centre/Center
[/LIST]


[SIZE="3"]**Playing Encrypted DVDs**[/SIZE]
[COLOR="#AAA"][SIZE="1"]Canonical, due to legal constraints, cannot actually provide you with the ability to play encrypted DVDs out of the included media. Below assumes you've installed the restricted-extras (if not, when you try to play a movie the program will prompt you to install the extras package anyway)[/SIZE][/COLOR]

[LIST=1]
[*] Open a Terminal Application
[*] enter...
[LIST]
[*](Under Jaunty)```
sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```
[*](Under Karmic)```
sudo wget http://www.medibuntu.org/sources.list.d/karmic.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```
[/LIST]
[*] Type your password if requested.
[*] Continue with the following Commands:
```
sudo apt-get install medibuntu-keyring
```
```
sudo apt-get update
```
[*] If using a 32-bit copy of *buntu:
```
sudo apt-get install w32codecs libdvdcss2
```
[*] If using a 64-bit copy of *buntu:
```
sudo apt-get install w64codecs libdvdcss2
```
[COLOR="#AAA"][SIZE="1"]If unsure, I believe installing the 32-bit codecs might still work. Attempt to play a Hollywood DVD, if it fails, remove the 32-bit codecs and install the 64-bit instead.[/SIZE][/COLOR]
[/LIST]


[SIZE="3"]**Getting sound working (should all else fail)**[/SIZE]
[COLOR="#AAA"][SIZE="1"]This tip involves your wallet. I found this when working with a Mac Pro; This also will monopolise 1 USB port.[/SIZE][/COLOR]

[LIST=1]
[*]If sound absolutely will not work, and your card is completely unsupported.
[*]Find a local computer store - preferably one that mostly sells computer parts instead of whole computers. There are just better chances of finding this part in these types of sellers.
[COLOR="#AAA"][SIZE="1"]Call and see if they have "USB Audio converters" if you have a phone handy.[/SIZE][/COLOR]
[*]But a "USB Audio Converter"; It has two jacks, one for headphones and another for speakers, regardless of the brand make or model. If it does not, avoid buying it. The part cost me, personally, ~$10 Canadian, so expect about ~$10 usd or however much the currency difference is in your area.
[*] When plugged into your computer, remember which port you plug it into, otherwise you'll be reconfiguring your sound settings should you move it.
[COLOR="#AAA"][SIZE="1"]Plugging a USB Audio adapter looks exactly like another sound card to your system, and it will treat it like a second sound card.[/SIZE][/COLOR]
[*] Reboot, it may be picked up as the default sound card. If not, use your favourite sound-configuration tool to select the USB dongle as your sound card. When looking for which sound card to choose, the name usually includes "USB ManufacturerName ModelNo" or something similar. You may need to enable "Advanced Sound Devices", depending on your program of choice.
[/LIST]

---

