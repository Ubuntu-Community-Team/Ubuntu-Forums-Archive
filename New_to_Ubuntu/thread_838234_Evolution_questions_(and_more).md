---
title: "Evolution questions (and more)"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by Alexbit on 2008-06-23
Hi all,
this is my first post on ubuntu...
I've bought an ethernet modem so I decide to try (seriously) Ubuntu.
I come from Windows environment.
I've installed ubuntu un my laptop Acer Aspire 1513LMi.
All seems to works fine but now I need some help.
First of all I have to move all my old Outlook data (No mail. Only Calender and contacts) on evolution.
I've exported Calendar and Contacts with "outport-1.1.25".
I'm to able to import agenda but unable to import contact. I don't know why. It seem that evolution import wizard do not recognize the file exported whit outport.
I also need to know the command to erase *all* evolution data.
When I use windows is it simple for me to set some aspect like the dimension of the border of a windows or the size of each character on windows but with ubuntu I can't.
I've only follow the way to change the skin but not each graphics parameter.

So... at the end... can some one help me?
Thank you in advance!
Ale

---

### Post by cmnorton on 2008-06-23
The simplest way for me to move contacts back and forth between Windows and Linux systems -- Outlook to Evolution -- is to find a tool to convert the email part, and then synch with my Palm. It sounds like you converted the email part. 

As I recall, Evolution wants a contacts format that in the end made me decide syncing would be easier.

---

### Post by the_doc on 2008-06-23
I usually recommend CSV files as they often do the trick.

Here is a blog post describing the process.  Not my blog, I dug it up on a search, but it saves me retyping everything.

[http://buranen.info/?p=157]("http://buranen.info/?p=157")

---

### Post by stchman on 2008-06-23
> **Alexbit said:**
> Hi all,
this is my first post on ubuntu...
I've bought an ethernet modem so I decide to try (seriously) Ubuntu.
I come from Windows environment.
I've installed ubuntu un my laptop Acer Aspire 1513LMi.
All seems to works fine but now I need some help.
First of all I have to move all my old Outlook data (No mail. Only Calender and contacts) on evolution.
I've exported Calendar and Contacts with "outport-1.1.25".
I'm to able to import agenda but unable to import contact. I don't know why. It seem that evolution import wizard do not recognize the file exported whit outport.
I also need to know the command to erase *all* evolution data.
When I use windows is it simple for me to set some aspect like the dimension of the border of a windows or the size of each character on windows but with ubuntu I can't.
I've only follow the way to change the skin but not each graphics parameter.

So... at the end... can some one help me?
Thank you in advance!
Ale

Outlook being a M$ product uses a proprietary .pst file format.  The easiest way I have found to export Outlook data is to use Thunderbird for the email and contacts portion.  Install Thunderbird on your Windows machine and it will export the settings for you into Thunderbird.  You will need to copy the folder that Thunderbird creates in Windows to a flash drive.

Once in Linux with Evolution I believe there is an import function and you simply point to the files.  Mind you it is not going to be a perfectly automatic process. 

I cannot help you with the calendar stuff.

Hope this helps.

---

### Post by the_doc on 2008-06-23
Microsoft also allows CSV files which most mail clients support.

---

### Post by Alexbit on 2008-06-25
> **Alexbit said:**
> Hi all,
this is my first post on ubuntu...
I've bought an ethernet modem so I decide to try (seriously) Ubuntu.
I come from Windows environment.
I've installed ubuntu un my laptop Acer Aspire 1513LMi.
All seems to works fine but now I need some help.
First of all I have to move all my old Outlook data (No mail. Only Calender and contacts) on evolution.
I've exported Calendar and Contacts with "outport-1.1.25".
I'm to able to import agenda but unable to import contact. I don't know why. It seem that evolution import wizard do not recognize the file exported whit outport.
I also need to know the command to erase *all* evolution data.
When I use windows is it simple for me to set some aspect like the dimension of the border of a windows or the size of each character on windows but with ubuntu I can't.
I've only follow the way to change the skin but not each graphics parameter.

So... at the end... can some one help me?
Thank you in advance!
Ale

So...
cause it's fast & simply I've used outport to export agenda from outlook.
There's an important benefit using Outport: It maintain the recursive appointment other method doesn't!

For contact's I've used the csv format but I've also try with multisync.
Each method works fine for me.
Thank you all for your help.

However I want to ask you again about the other question I've write down in my post.

I'm sure that someone can understand my problem (caused by "win" dependences - till now...).

Thank you again
Ale

---

