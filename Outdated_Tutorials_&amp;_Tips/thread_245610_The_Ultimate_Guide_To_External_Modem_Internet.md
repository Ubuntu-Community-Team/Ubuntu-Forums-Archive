---
title: "The Ultimate Guide To External Modem Internet"
date: 2006-08-28
forum: Outdated Tutorials &amp; Tips
---

### Post by CameronCalver on 2006-08-28
[FONT="Arial Black"]**[SIZE="2"]This is the ULTIMATE guide to modem confuration and getting onto the www[/SIZE]**[/FONT]
[COLOR="Red"]
[FONT="Arial Black"]**[SIZE="2"]Firstly getting the information which you will require[/SIZE]**[/FONT][/COLOR]

**[FONT="Arial Black"][COLOR="Red"]1.[/COLOR] Your ISP's Phone number eg myn is 0198379000[/FONT]**
[FONT="Arial Black"]**[COLOR="Red"]2.[/COLOR] your username and password for your isp myn is calversh*** and my password is ******** (lol you didnt think you really were getting it did you)**[/FONT]
[FONT="Arial Black"]**[COLOR="Red"]3.[/COLOR]the location of your device which i will tell you ow to get later**[/FONT]
[FONT="Arial Black"]**[COLOR="Red"]4.[/COLOR]Your ISP's DNS address myn is 203.0.178.191**[/FONT]
[FONT="Arial Black"]Use this command to make a folder to put the scripts in****[/FONT]
```
sudo mkdir /internetscript
```
[FONT="Arial Black"]Now use this command to create a script****[/FONT]

[COLOR="Red"][FONT="Arial Black"][SIZE="2"]**Firstly Obataining the location of your modem**[/SIZE][/FONT][/COLOR]
[FONT="Arial Black"]This is done very easyly firstly plug it into a serial port or a com port and go to [COLOR="Red"]System--->Administration---->Networking----Propterties on Modem Connection[/COLOR][/FONT][FONT="Arial Black"]** (Hope fully the modem is even there or i'd be going to a different thread or buying another modem)**[/FONT][FONT="Arial Black"][COLOR="Red"]Then the Modem tab and click auto detect then remember that output myn was /dev/ttyS0[/COLOR][/FONT]
[FONT="Arial Black"][COLOR="Red"]**[SIZE="2"]Next you have to set up ppp Open up a terminal and type ```
[COLOR="Black"]Sudo ppp[/COLOR]
```At the main arror to Create a Connection then[/SIZE]**[/COLOR][/FONT]
[FONT="Arial Black"]**[COLOR="Red"][SIZE="2"]1.[/SIZE][/COLOR]**[/FONT][FONT="Arial Black"]Leave leave the name as Provider[/FONT]
[FONT="Arial Black"]**[COLOR="Red"][SIZE="2"]2.[/SIZE][/COLOR]**[/FONT][FONT="Arial Black"]Arrow to Dynamic Use Dynamic DNS then hit "Ok"[/FONT]
[FONT="ArialBlack"]**[COLOR="Red"][SIZE="2"]3.[/SIZE][/COLOR]**[/FONT][FONT="Arial Black"]Type in your Primary DNS that you got from your isp and if you did not get a secondary Ip do not worry it does not affect the proccess at all
**[COLOR="Red"][SIZE="2"]4[/SIZE][/COLOR]**[/FONT][FONT="Arial Black"]Then Go to Pap Peer Authentication Protocol and hit enter[/FONT]
[FONT="Arial Black"]**[COLOR="Red"][SIZE="2"]5.[/SIZE][/COLOR]**[/FONT][FONT="Arial Black"]Enter your username and password that you got from your ISP[/FONT]
[FONT="Arial Black"]**[COLOR="Red"][SIZE="2"]6.[/SIZE][/COLOR]**[/FONT][FONT="Arial Black"]Leave the speed at 115200 as default[/FONT]
[FONT="Arial Black"]**[COLOR="Red"][SIZE="2"]7.[/SIZE][/COLOR]**[/FONT][FONT="Arial Black"]Choose Tone or Pulse Dialing i would use Tone and if it does not work try pulse[/FONT]
[FONT="Arial Black"]**[COLOR="Red"][SIZE="2"]8.[/SIZE][/COLOR]**[/FONT][FONT="Arial Black"]Enter the phone number[/FONT]
[FONT="Arial Black"]**[COLOR="Red"][SIZE="2"]9.[/SIZE][/COLOR]**[/FONT][FONT="Arial Black"]CLick manual port configuraion and enter in that code you got from the gnome networking application[/FONT]
[FONT="Arial Black"]**[COLOR="Red"][SIZE="2"]10[/SIZE][/COLOR]**[/FONT][FONT="Arial Black"]Click Write Changes then exit the program[/FONT]

[FONT="Arial Black"][COLOR="Red"]**[SIZE="2"]Testing[/SIZE]**[/COLOR][/FONT]
[FONT="Arial Black"]Now to test it with this command
```
pon
```[/FONT][FONT="Arial Black"]**And this command to disconnect **[/FONT][COLOR="Black"]```
poff
```[/COLOR]
[FONT="Arial Black"]Now to to create a folder to put the scripts in****[/FONT]
```
sudo mkdir /internetscript
```
[FONT="Arial Black"]**Next to create the scripts, Use this command to create a script file in that resently creaed directory**[/FONT]
```
sudo gedit /internetscript/on
```
[FONT="Arial Black"]Now insert this in the empty file****[/FONT]
```
!# /bin/bash
        pon
```
[FONT="Arial Black"]Now We need to create a script to turn the internet off****[/FONT]
```
sudo gedit /internetscript/off
```
[FONT="Arial Black"]Then insert this is****[/FONT]
```
!# /bin/bash
         poff
```
[FONT="Arial Black"]now we need to make these files executable use these commands****[/FONT]
```
sudo chmod +x /internetscript/on
```
[FONT="Arial Black"]and****[/FONT]
```
sudo chmod +x /internetscript/off
```
[FONT="Arial Black"]Then All you have to do is make a lancher to /internetscript/on or off and you will have internet in no time  so you can add a lancher from desktop or from the lancher panel****[/FONT]


[FONT="Impact"][SIZE="2"]**By Cameron**[/SIZE][/FONT]

---

