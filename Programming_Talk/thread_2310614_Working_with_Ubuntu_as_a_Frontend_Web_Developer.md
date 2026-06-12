---
title: "Working with Ubuntu as a Frontend Web Developer"
date: 2016-01-20
forum: Programming Talk
---

### Post by stefan_03 on 2016-01-20
Hello folks,

I started using Ubuntu around 3 years ago (Dual Boot with Windows 7). Back then, I was kind of finishing my bachelor degree course for business information systems. As a side job, I worked on some websites and blog systems. I was setting up the websites and adapted their styles to the predefined design. Time went by and I started working for an IT company, I began as a freelancer in the web development department. I created web sites, focusing on the CSS styling parts. Everything began to be professional. I realized pretty soon how amazing it is to have Linux. The terminal is great for tools like git and CLI tools like grunt, etc. - whenever I help out workmates setting up git, grunt, sass, etc. I almost freak out. It is really complicated and things do not work. Another great thing about Ubuntu is, that the file manager (Nautilus) has the ability to "mount" FTP webspace, and you can add common used FTP connections to your favourites. It's great when you want to quickly upload an image to an FTP server.

Major tools like Atom, Sublime, WebStorm, IntelliJ or even Visual Studio Code, they all work very well with Linux.

The only problem I have is related to proprietary software used by the designers. I get e.g. a PSD file and should adapt the web Frontend to the design. A good friend of mine is designer, and I always send it to her so that she creates a PDF and exports the single layers out of it. GIMP often fails doing that. As Adobe tools are not available for Linux users, I sometimes have problems when I get PhotoShop or InDesign files. And it is sometimes annoying that I have to explain that my OS does not run tools like these and the designers should send me the new files - and they do not have a clue how to use their tools, and then I am sitting at the client's office for a few hours and I can't start to work.

I am thinking about buying a one-person licence for the Adobe Suite, and running Windows on a virtual machine, opening these files. I am not very confident with this solution, but it seems to be the most cozy one. What do you think about it? Any front end web developers here, who experienced similar things? Any better solutions? Are there good tools that open .psd and .indd and .fw.png files? (I am okay with readonly tools, and if they cost, I would be fine too) 

I'm looking forward to reading about your experiences :)


Stefan

---

### Post by Dimarchi on 2016-01-23
From my personal, subjective, and limited experience, I have found out that the answer is no. Dual boot with Windows and those applications installed is still your (better) friend, in my humble opinion...and that what it is, an opinion. How the set up you described works (virtual Windows), I can not say - I have no useful work related experience of that. The opposite, virtual Ubuntu under Windows, that works well. Now speaking from experience gained during real work.

I would like to hear from other people, too. I doubt we are the only ones who have wrestled with this particular problem.

---

### Post by SeijiSensei on 2016-01-23
I run Win7 quite successfully in a VirtualBox on top of Ubuntu.  If you need to interact with colleagues who use things like Photoshop it seems like a fine solution to me.

If you need to move files from the one platform to the other, you can use the "shared folders" feature in VirtualBox.  You'll need to install the Extension Pack to enable that.  I also have a networked file server in my home office, so I usually store everything there.  Both operating systems can see the files on the server, using Samba for the Windows machine and NFS for Linux.

> **stefan_03 said:**
> The only problem I have is related to proprietary software used by the designers. I get e.g. a PSD file and should adapt the web Frontend to the design. A good friend of mine is designer, and I always send it to her so that she creates a PDF and exports the single layers out of it. GIMP often fails doing that.

I'm afraid I don't really understand what you're saying here.  GIMP can import and export .psd files, so why is a PDF involved?  GIMP can also certainly assemble and disassemble layers, too.  Where does it "fail?"

---

### Post by stefan_03 on 2016-01-24
Hello, thanks for your opinions. I will really try to install Win7 or Win10 on a virtual machine, let's see how it works.

> [COLOR=#000000]GIMP can import and export .psd files, so why is a PDF involved? GIMP can also certainly assemble and disassemble layers, too. Where does it "fail?"
[/COLOR]It does not display the exact layout of the single layers properly. It's 90% good, but I need to know how the _exact_ result should look like. 

The good thing about a Virtual Machine would be: if Windows stops working, I take a backup of the .vdi file and everything's fine. Plus, I can use this on multiple computers.

---

