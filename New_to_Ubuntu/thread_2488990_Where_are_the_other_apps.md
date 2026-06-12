---
title: "Where are the other apps?"
date: 2023-07-14
forum: New to Ubuntu
---

### Post by lwalper on 2023-07-14
When I enter the Ubuntu Software tab there is a list of popular apps available for download. Then, at the bottom of the list there is a section of "categories" with active links, but when I click on the link a box opens with several empty boxes with ... in the center. Are there supposed to be any more software apps under those categories? -- or maybe I'm doing something wrong?? -- or maybe I just need to give it time to populate the screen??

---

### Post by TheFu on 2023-07-15
If you want to see everything, use **Synaptic** for your package manager.  Or you can use the shell program, **apt**.

Apt is already on your system. Access it by opening a terminal.

Synaptic probably isn't installed, but it is in the official repos.  "Software Center" is the dumbed down package manager.

How are you "new to ubuntu", but using an account from 2007?

---

### Post by lwalper on 2023-07-15
> **TheFu said:**
> How are you "new to ubuntu", but using an account from 2007?
Been playing with it off and on looking for an alternative to Windows, but have never really settled down here due to the paucity of competitive Windows-similar apps (like the Adobe Suites, Quickbooks, AutoCAD, various Bible apps) and confusion at the CLI. I'd like to set up a file server Proxmox but have been told I need to get more familiar with the Linux CLI which has been a bit of a struggle for me. I was somewhat familiar with DOS (3.3.1 and 5.1), but for some reason the Linux CLI has been somewhat daunting. Most online videos and training courses have been assembled with the incorrect assumption that the student (me) has some basic understanding of nomenclature, but just using the {ls} command has it pitfalls. In Proxmox, the system loads to the CLI, but when the {ls} command issued I get and unknown command warning (or something to that effect). Seems like there ought to be something in that folder. So I {cd ..} back one level, the CLI appears to be unchanged, but the {ls} command now presents files/folders, and whatnot. I'll keep plugging along. If you know of any BEGINNER tutorials let me know. I'm still on the steep learning curve of "what do I do next?"

---

### Post by TheFu on 2023-07-15
Work through this book. [https://www.linuxcommand.org/tlcl.php](https://www.linuxcommand.org/tlcl.php)

Start with Chapter 1 and do the first 12 chapters.  Do all the exercises. Do the extra exercises.  Join a LUG and attend every meeting they have just to hear other Linux people talk. Don't worry if you don't understand everything.

Don't use any other references until you've worked through those first 250-ish pages.  Stay on task.  Use Linux daily, for everything.  1 hour a day, use Windows for the stuff you can't figure out how to do on Linux.  Failure is the best teacher.

The list of apps you posted don't have versions for linux, so you'll either need to keep Windows around for them, or you'll need to migrate to a native app that does enough of what you need. That's a personal choice.  I still use Windows for my accounting software too.  I won't use Adobe products. [https://blog.jdpfu.com/2010/06/30/why-are-you-still-using-adobe-tools](https://blog.jdpfu.com/2010/06/30/why-are-you-still-using-adobe-tools)

Proxmox is one of those things that seems easier, but isn't. If you want KVM/QEMU virtualization, use virt-manager or if you want bonehead virtualization, try Gnome "Boxes".

---

### Post by lwalper on 2023-07-16
OK, thanks. I'll check it out.

---

### Post by lwalper on 2023-07-16
I've downloaded that reference - it looks good -- and readable (understandable). Thanks again! I understand your concerns with Adobe, but there just isn't any good alternative for InDesign or Photoshop. I'm doing anything I can to preserve my licensed copies of CS3 with OS HDD cloning (Clonezilla - a Linux tool) instead of transitioning to the ridiculous and $$$ subscription model -- and have disabled Javascript (and other stuff).

---

### Post by TheFu on 2023-07-16
> **lwalper said:**
> I've downloaded that reference - it looks good -- and readable (understandable). Thanks again! I understand your concerns with Adobe, but there just isn't any good alternative for InDesign or Photoshop. I'm doing anything I can to preserve my licensed copies of CS3 with OS HDD cloning (Clonezilla - a Linux tool) instead of transitioning to the ridiculous and $$$ subscription model -- and have disabled Javascript (and other stuff).

If you make money using Adobe stuff, I'd never say NOT to keep using them.  But if you don't, there are alternatives for almost anything, even if we don't like those alternatives initially.

---

### Post by lwalper on 2023-07-16
I've looked at GIMP as well as some "alternatives" (that really don't work well) as a replacement for InDesign. I think I'm pretty well stuck with that for book publishing. There's QuarkExpress, still a little pricy since I already have the Adobe Suite, but they do have a one-time licensing plan.

---

### Post by TheFu on 2023-07-16
> **lwalper said:**
> I've looked at GIMP as well as some "alternatives" (that really don't work well) as a replacement for InDesign. I think I'm pretty well stuck with that for book publishing. There's QuarkExpress, still a little pricy since I already have the Adobe Suite, but they do have a one-time licensing plan.

Yep, the Unix way would be to use latex for typesetting needs. I thought most publishers had a template for MS-Word they wanted used?
[https://tex.stackexchange.com/questions/19497/how-do-you-setup-a-tex-document-to-self-publish-a-book-online](https://tex.stackexchange.com/questions/19497/how-do-you-setup-a-tex-document-to-self-publish-a-book-online) might be useful.

I don't need to control page layout and when I worked at a publisher, we only accepted PDF from our clients.  So people could use any tool they wanted.  Just before I got there, they were still accepting PS files, but that wasn't a full enough definition like PDF is. We were more about graphical publishing, not so much text/articles.

I can completely understand using InDesign.  I assume you've been to [https://alternativeto.net/](https://alternativeto.net/) to seek out Linux alternatives to the tools you've been using on other platforms?
For example: [https://alternativeto.net/software/adobe-indesign/](https://alternativeto.net/software/adobe-indesign/)  says to check out Scribus.  

I still use Visio occasionally, though there are other options on Linux, I have 10+ yrs experience with Visio, so I keep a WinXP virtual machine around just for it and MS-Office stuff.  That WinXP system also has some games.  Perhaps once a year, I want to create a quick Visio diagram and it is faster for me to spin up the VM than to learn some new tool.  I made my living drawing technical/archtecture diagrams.

---

### Post by lwalper on 2023-07-16
Some time back I looked a Scribus which didn't really seem to fit my needs. I just looked a [Affinity Publisher]("https://alternativeto.net/software/affinity-publisher/about/") which looks pretty good, and the price is certainly right. IngramSpark has quit accepting the older ID files, but do take the PDFs so that's what they get from us, including PDF CMYK covers. I also keep a WinXP VM for AutoCAD 2000 Architectural Desktop (yep, more than 20 years old and it doesn't play well with Win10, but the VM works great).

---

### Post by lwalper on 2023-07-19
So, as I am working through the [recommended "The Linux Command Line" reading]("https://www.linuxcommand.org/tlcl.php") I come to things like "Finally, using the  command line, we will create a few files:"

and on page 11 I am instructed to enter the following at the command line

```
me@linuxbox: ~/playground $ touch file1 file2 "ugly file"
```

which I do {me@linuxbox: ~/playground $ touch file1 file2 "ugly file"} (without the curly brackets), press enter, and nothing happens. I scratch my head, re-enter the text, checking for typos -- and nothing happens. I then, after several frustrating attempts decide that the instruction should have *actually* said,

At the command line enter ```
touch file1 file2 "ugly file"
```That works. Go figure.

---

### Post by TheFu on 2023-07-19
In the nomenclature section of the book - guess you skipped that part - it is clear that 
**$** is for a normal userid
**#** is for the root userid
Commands after those characters should be entered as shown.
I suppose it could be confusing since the # is also a very common comment delimiter, so context matters.  With Ubuntu, we don't really use the root account, so most commands with elevated privileges should be entered as
```
$ sudo command options
```
You may see similar in nomenclature across the web, since all Unixen have the same expectations about userids running commands.

Also, learn that every shell has a prompt and that prompt is extremely useful.  While you can customize the prompt - go crazy if you like - the default creates exactly the information that scp and rsync need to transfer files.


BTW, I see an error in your copy of 
```
me@linuxbox**: ~/p**layground $ touch file1 file2 "ugly file"
```
I bet it was
```
me@linuxbox**:~/p**layground $ touch file1 file2 "ugly file"
```

Spaces matter, since space(s) is the delimiter for most shells, unless you change it.

In general, Unix says nothing when something that doesn't need output completes successfully and failures get an error message.  No news is good news.

One last thing.  If you don't understand something or think it isn't working correctly, it is best to assume it is your mistake first and not a mistake by others. You are new and things that are working perfectly as intended don't always fit into our idea for what should happen.

---

### Post by lwalper on 2023-07-19
OK. Thanks. Carry on.

So I should enter the $ -- or is that just given to indicate that I'm at the prompt for the normal userid?

---

### Post by TheFu on 2023-07-20
> **TheFu said:**
> In the nomenclature section of the book - guess you skipped that part - it is clear that 
**$** is for a normal userid
**#** is for the root userid
_**Commands after those characters should be entered as shown.**_ 

Answered above.

---

