---
title: "[Solved] ICS on Ubuntu"
date: 2009-05-07
forum: Philippine Team
---

### Post by SHENGTON on 2009-05-07
Hello guys, good evening. ;)

I have here two desktop computers and one laptop computer.

Here's my current setup:
Router <--> PC 1 (My Dad's desktop computer) (Windows XP)
        |<---> PC 2 (My desktop computer) (Ubuntu Jaunty) <---> Laptop computer (Windows Vista Starter)

My computer has two LANcards. I don't want to buy a switch. All I want is to share my Internet connection to my mother's laptop by using ICS. But since I'm newbie with this I don't know what settings should I configure.

Anyone can help?

Take care and God bless. :)

---

### Post by Script Warlock on 2009-05-07
> **SHENGTON said:**
> Hello guys, good evening. ;)

I have here two desktop computers and one laptop computer.

Here's my current setup:
Router <--> PC 1 (My Dad's desktop computer) (Windows XP)
        |<---> PC 2 (My desktop computer) (Ubuntu Jaunty) <---> Laptop computer (Windows Vista Starter)

My computer has two LANcards. I don't want to buy a switch. All I want is to share my Internet connection to my mother's laptop by using ICS. But since I'm newbie with this I don't know what settings should I configure.

Anyone can help?

Take care and God bless. :)

1 built-in and a pci lancard para sa tatlong pc? y cable is the solution pero di pwede sabay gamit sa inet dapat naka shutdown ang pc2 kapag nakasindi ang laptop...settings i can only share for ubuntu..

---

### Post by dodimar on 2009-05-08
> **SHENGTON said:**
> Hello guys, good evening. ;)

I have here two desktop computers and one laptop computer.

Here's my current setup:
Router <--> PC 1 (My Dad's desktop computer) (Windows XP)
        |<---> PC 2 (My desktop computer) (Ubuntu Jaunty) <---> Laptop computer (Windows Vista Starter)

My computer has two LANcards. I don't want to buy a switch. All I want is to share my Internet connection to my mother's laptop by using ICS. But since I'm newbie with this I don't know what settings should I configure.

Anyone can help?

Take care and God bless. :)

wala bang wireless capability yung router mo? yung diagram mo is your "current" setup.. so na isetup mo na... how did you share the net from PC2 to Laptop? it'll be the same way na gagawin mo sa laptop ng mother mo.

---

### Post by kingkalag on 2009-05-08
if I were you i'll invest into a new router if your router dosent have a wireless capability, knowing how to ICS is good but remember if your system is off your mom wont have internet connection, but thats just me.  /.

---

### Post by dodimar on 2009-05-08
> **kingkalag said:**
> if I were you i'll invest into a new router if your router dosent have a wireless capability, knowing how to ICS is good but remember if your system is off your mom wont have internet connection, but thats just me.  /.

Yup.. I agree... magkano router ngaun? 1500 pesos for already a good router..

since mukang madaming gumagamit ng net sa inyo.. share share kayo... pare pareho naman kayong makikinabang.. :)

---

### Post by pinoyskull on 2009-05-08
cable is messy, go for the wireless router

---

### Post by SHENGTON on 2009-05-08
Hello guys, good afternoon. :)

These two methods work well for me without using firestarter:

**First Method:**
1. Right-click on the network icon and click "Edit Connections".
2. In "Wired" tab, select the Marvell network card and click Edit.
3. In &#8220;IPv4 Settings&#8221; tab, select &#8220;Shared to other computers&#8221; and click OK.
4. Now, plug the cable to your Ubuntu computer to Windows XP computer.
5. In Ubuntu computer, click on the nm-applet or network icon and select Marvel network card you have just created. In few seconds, a popup balloon message from the nm-applet or network icon says "Connection is established".

**Second Method:**
1. Right-click on the network icon and click "Edit Connections".
2. In "Wired" tab, click "Add" button.
3. In "Connection name" type "ICS" or any name what you want.
4. Uncheck "Connect automatically".
5. In &#8220;IPv4 Settings&#8221; tab, select &#8220;Shared to other computers&#8221; and click OK.
6. Now, plug the cable to your Ubuntu computer to Windows XP computer.
7. In Ubuntu computer, click on the nm-applet or network icon and select "ICS" you have just created. In few seconds, a popup balloon message from the nm-applet or network icon says "Connection is established".

Take care and God bless. :)

---

### Post by kingkalag on 2009-05-08
are you telling us how to or your saying that you've solved your problem.  /.

---

### Post by loell on 2009-05-08
> **kingkalag said:**
> are you telling us how to or your saying that you've solved your problem.  /.

haha, both from the looks of it :D, this thread is solved I guess.

---

### Post by SHENGTON on 2009-05-08
Hello kingkalag, good afternoon. :)

My problem is already solved using those two methods I posted.

Take care and God bless. :)

---

### Post by kingkalag on 2009-05-08
so to make the story short you didn't search before asking for help.
anyhow good for you that find answers for your own questions.

Good Luck 

$ exit

---

### Post by SHENGTON on 2009-05-08
Hello kingkalag, good evening. :)

Definitely, of course I searched before asking for help here. First I found an article from the documentation of Ubuntu Jaunty which is "Internet/Connection Sharing" but it looks complicated, too many commands. Then in that documentation it is said as well about "firestarter". I tried and troubleshoot it for 30 minutes but it just wouldn't work. So I tried to post here kung meron pang ibang paraan. So while leaving my post here, I'm searching as well just hoping if there's another way. But fortunately for three hours of searching using google and yahoo search engines, I found an article from a [blog site]("http://blog.chewearn.com/2009/01/28/internet-connection-sharing-in-ubuntu-intrepid/") and it looks more easy than the documentation. It was almost 1am in the morning nong makita ko na yong solution and applied it immediately. 

The first method, that's the method that I applied first and it worked. The second method is mine. I just changed something based on the first method and it worked as well.

Take care and God bless. :)

---

### Post by ragadanga63 on 2009-05-08
I still think a wireless router will be the best option.  Hehehe...

---

### Post by dannybuntu on 2009-05-10
> **SHENGTON said:**
> Hello guys, good afternoon. :)

These two methods work well for me without using firestarter:

**First Method:**
1. Right-click on the network icon and click "Edit Connections".
2. In "Wired" tab, select the Marvell network card and click Edit.
3. In &#8220;IPv4 Settings&#8221; tab, select &#8220;Shared to other computers&#8221; and click OK.
4. Now, plug the cable to your Ubuntu computer to Windows XP computer.
5. In Ubuntu computer, click on the nm-applet or network icon and select Marvel network card you have just created. In few seconds, a popup balloon message from the nm-applet or network icon says "Connection is established".

**Second Method:**
1. Right-click on the network icon and click "Edit Connections".
2. In "Wired" tab, click "Add" button.
3. In "Connection name" type "ICS" or any name what you want.
4. Uncheck "Connect automatically".
5. In &#8220;IPv4 Settings&#8221; tab, select &#8220;Shared to other computers&#8221; and click OK.
6. Now, plug the cable to your Ubuntu computer to Windows XP computer.
7. In Ubuntu computer, click on the nm-applet or network icon and select "ICS" you have just created. In few seconds, a popup balloon message from the nm-applet or network icon says "Connection is established".

Take care and God bless. :)

I have the same problem. We both don't want to buy a router. :)

I have been having [this problem]("http://dannybuntu.blogspot.com/2009/05/day-984b-our-local-area-network.html") for 1 week already.

I am happy for you Shengton because you succeeded in making a solution that does not involve buying something. 

So to all router salesmen here, I am sorry but I don't have cash to buy a router.

---

### Post by dodimar on 2009-05-10
> **dannybuntu said:**
> I have the same problem. We both don't want to buy a router. :)

I have been having [this problem]("http://dannybuntu.blogspot.com/2009/05/day-984b-our-local-area-network.html") for 1 week already.

I am happy for you Shengton because you succeeded in making a solution that does not involve buying something. 

So to all router salesmen here, I am sorry but I don't have cash to buy a router.

I am sorry but we are NOT ROUTER SALESMAN!!!!

If you think we were suggesting something for our own gain, then you are DEFINITELY WRONG!!!

What we were suggesting is the most practical and economical way of sharing internet... :mad:

tagal kong di na-check forums tapos ito pa mabungaran ko...

---

### Post by kingkalag on 2009-05-10
ang sakit sa ulo ng thread na ito. 

this thread is TITLED: ICS on UBUNTU


#SHENGTON 1st Post
> **SHENGTON said:**
> Hello guys, good evening. ;)

I have here two desktop computers and one laptop computer.

Here's my current setup:
Router <--> PC 1 (My Dad's desktop computer) (Windows XP)
        |<---> PC 2 (My desktop computer) (Ubuntu Jaunty) <---> Laptop computer (Windows Vista Starter)

My computer has two LANcards. I don't want to buy a switch. All I want is to share my Internet connection to my mother's laptop by using ICS. But since I'm newbie with this I don't know what settings should I configure.

Anyone can help?

Take care and God bless. :)

and I'll Make it CLEAR.   He or She is ASKING for HELP. Dodimar and I only suggested that hes better off getting a router if hes router dosent have a wireless capability.

Read between SHENGTON 1st and 2nd post cause no one ever mention to use firestarter or how to //

#SHENGTON 2nd Post
> **SHENGTON said:**
> Hello guys, good afternoon. :)

These two methods work well for me without using firestarter:

**First Method:**
1. Right-click on the network icon and click "Edit Connections".
2. In "Wired" tab, select the Marvell network card and click Edit.
3. In “IPv4 Settings” tab, select “Shared to other computers” and click OK.
4. Now, plug the cable to your Ubuntu computer to Windows XP computer.
5. In Ubuntu computer, click on the nm-applet or network icon and select Marvel network card you have just created. In few seconds, a popup balloon message from the nm-applet or network icon says "Connection is established".

**Second Method:**
1. Right-click on the network icon and click "Edit Connections".
2. In "Wired" tab, click "Add" button.
3. In "Connection name" type "ICS" or any name what you want.
4. Uncheck "Connect automatically".
5. In “IPv4 Settings” tab, select “Shared to other computers” and click OK.
6. Now, plug the cable to your Ubuntu computer to Windows XP computer.
7. In Ubuntu computer, click on the nm-applet or network icon and select "ICS" you have just created. In few seconds, a popup balloon message from the nm-applet or network icon says "Connection is established".

Take care and God bless. :)

if you found answers to your problems somewhere else just post the link or "PROBLEM SOLVED" coz your making yourself look stupid. 
... .. .

---

### Post by kingkalag on 2009-05-10
> **dannybuntu said:**
>  
So to all router salesmen here, I am sorry but I don't have cash to buy a router.

heres a line for you "theres only 10 kinds of person who knows how to read binary one who does and one who dosent"... .. .

---

