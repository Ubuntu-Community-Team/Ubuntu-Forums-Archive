---
title: "develop application on sony ericsson k750i, how?"
date: 2010-05-16
forum: Programming Talk
---

### Post by c174 on 2010-05-16
Hi, I want to able to develop programs for my cellphone - a Sony Ericsson k750i.

Here is what my project is about:

* I'm building an electronic "measuring tape". The tape itself is opaque and with holes that are distributed with a regular spacing. Using a couple of opto-switches and a microprocessor (PIC16F627) it is possible to keep track of the position along the tape.

* At the moment I have interfaced the microprocessor with the RS232 port on my desktop computer using a MAX232 chip. I use Python-Serial to open and read from the port. So far so good.

* The final goal is to store measurements of position and time in a file, which can then later be postprocessed.

Now comes my problem. I want to make my application mobile. I could use a laptop, but still this is not very handy considering that I'm going to use the measuring setup in a rowing boat:) So I got the idea to use my cellphone instead... However, I'm stuck on this problem:

1) How do I program the k750i?

I tried to search the web but didn't real find the information I need. I only found out that k750i is running Java, and ther's an SDK for Windows on the Sony Ericsson website. I was hoping I could develop the software on Ubuntu?

It seems many cellphones can understand "AT commands", but I didn't manage to figure out how that works and if I could use that?

---

### Post by DangerOnTheRanger on 2010-05-16
Do you have any experience in embedded programming? It's pretty hard, *trust me.. :(*
Try developing with the Lego NXT kit first, with the LeJOS operating system, to get a little experience with embedded stuff.

---

### Post by c174 on 2010-05-16
> **DangerOnTheRanger said:**
> Do you have any experience in embedded programming? It's pretty hard, *trust me.. :(*
Try developing with the Lego NXT kit first, with the LeJOS operating system, to get a little experience with embedded stuff.

I'm not sure about the exact definition of embedded programming, but I managed to program the PIC-chip in assembly (using Piklab and a Velleman board). So it is not that nothing is working:)

I "just" need to exchange the PC with my cellphone...

---

### Post by c174 on 2010-05-22
In case anybody else needs this, here's a little recipe that worked for me:

1) Install Netbeans - make sure JavaME is included in the package
2) Go the Sony Ericsson's developer page and download and install the SDK
3) Start up Netbeans and go to Tools -> Java Platforms and add the ones detected from Sony Ericsson
4) Now from the Start Page in Netbeans click your way to a tutorial on mobile applications
5) Once the you have an application working in the emulator, change the target to match your cell phone type (select a target without _Emu in the name)
6) Plug your phone to the computer via USB
7) Browse to the folder MSSEMC/Media Files/other and put the *.java file in here (the application java-file)
8) Unplug the phone
9) On the phone browse to Files/other and click "Install" on the application file, select a location where to install it
10) Go to where you installed the program and click it to see it in action. You might need to press "arrow back" for a second or more to quit the program.

These steps worked for me on a Windows machine. I guess something similar works on Linux.

---

### Post by .:PiXi²:. on 2010-05-22
> **c174 said:**
> In case anybody else needs this, here's a little recipe that worked for me:

1) Install Netbeans - make sure JavaME is included in the package
2) Go the Sony Ericsson's developer page and download and install the SDK
3) Start up Netbeans and go to Tools -> Java Platforms and add the ones detected from Sony Ericsson
4) Now from the Start Page in Netbeans click your way to a tutorial on mobile applications
5) Once the you have an application working in the emulator, change the target to match your cell phone type (select a target without _Emu in the name)
6) Plug your phone to the computer via USB
7) Browse to the folder MSSEMC/Media Files/other and put the *.java file in here (the application java-file)
8) Unplug the phone
9) On the phone browse to Files/other and click "Install" on the application file, select a location where to install it
10) Go to where you installed the program and click it to see it in action. You might need to press "arrow back" for a second or more to quit the program.

These steps worked for me on a Windows machine. I guess something similar works on Linux.

These steps also worked for me, on a W880i.

---

