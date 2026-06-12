---
title: "general how-to on converting old proprietary formats"
date: 2007-11-19
forum: Programming Talk
---

### Post by intelligentfool on 2007-11-19
So this is probably a bit ambitious, but i need some general advice. A friend works at a small company that is locked into a 10yr old piece of software that constantly is crashing on them, forcing windows reboots, etc. I know i'll need to find out more about the application, how they use it, and what they'd like to be able to do in the future,... but for now i'd like some general advice from the expert programmers that i'm sure frequent this board on how to go about such a task. 

My first thoughts are to make a disk image, since they dont have a backup at all currently. Then i could try to figure out how the files are formatted myself and go from there and try to script something out. 

anyway, any help would be great. sorry if this post isnt exactly clear, its monday morning and i'm a bit hungover :)

---

### Post by pmasiar on 2007-11-19
well, I think simplest suggestions will be to drink some coffee or tea and write more details, in more coherent way. But even before that, make a backup. :-)

---

### Post by intelligentfool on 2007-11-19
yea, my brain is functioning enough to know a full disk image would be a really good idea before i do anything else to their main customer database :)

---

### Post by aks44 on 2007-11-19
So basically you're willing to reverse-engineer an old, unsupported app huh? Oh well, good luck with that, you oughta be quite dedicated if you want to succeed...


IMHO the first thing to do is to determine if the application in question really uses a home-made proprietary format, or some (old) database engine or whatever.

On any platform (Linux, Win32, DOS/Win16, ...) there are tools to inspect a program binary (ELF, PE, MZ, ...) and know the shared libraries it uses / what functions it imports. That may give you useful hints.

If you're lucky you may find that the file format is well known, and with even more luck you may also find a ready-to-use library that is able to handle it.


However if this is indeed a home-made proprietary file format, you'll have to carefully reverse-engineer it. If you can, start with an empty database (your valuable data is backup'ed anyway, right?). Add *_a single_* entry, check for differences. Modify that entry, check again. Always one field at a time.

If it gets really tricky, you may want to disassemble & trace (most disassemblers/debuggers I know have the possibility of stopping a program whenever you want and step from there).


Once you know the original file format, better migrate the data to a well known database architecture (MySQL or SQLite come to mind...). From there it should be pretty straightforward (although time-consuming) to rewrite an application to handle this data. Making targeted (as opposed to generic) CRM / ERP applications is not very difficult (but again, it takes time), at least if you leave the "planning" part out of ERP. Making it network-aware is a whole different matter though, as it requires way more work.


Hope this helps a bit.

---

### Post by intelligentfool on 2007-11-19
yea, this is the kind of advice i was looking for. I obviously havnt been able to look the file binaries yet, but when i do, what are some of the tools you mentioned? I'm kind of hoping the company that made this app was lazy and used an off the shelf database engine, but we'll see. 

anyway, thanks.

---

### Post by mips on 2007-11-19
Out of curiosity, what is the application called and who made it ?

---

### Post by intelligentfool on 2007-11-19
its called "Leads Express" by Northwood Enterprises. I googled around a bit but couldnt find anything on either the company or the app. I'm not even sure if they're still in business honestly.

---

### Post by aks44 on 2007-11-19
> **intelligentfool said:**
> what are some of the tools you mentioned?

**_For Win32 (PE) apps:_**
- [IDA]("http://www.datarescue.com/idabase/") is definitely the ultimate debugger IMHO (but it costs like 350€ / $500).
- when it comes to examining PE internals (imports etc) the Win32 SDK has a quick & dirty tool (IIRC it is called "Dependency viewer", I can't check right now since I don't have Windows at home anymore)

**_For Linux (ELF) apps:_**
- not sure about the exact capabilities, but **gdb** is the de-facto standard debugger on Linux, and it has plenty of frontends.
- **ldd** should be able to inform you about dependencies / imports.

**_For old DOS/Win16 (MZ) apps:_**
Ahem, I used such tools long ago. If only I wasn't senile... :oops:
But IIRC IDA can also debug them. Don't quote me on that though, better double-check before throwing cash at it.



The first step being to identify exactly which type of binary you're dealing with (platform, OS?).

---

### Post by intelligentfool on 2007-11-19
I was told this app is running on a Win95 machine. that in mind, the HDD cant be more than a few gigs, so i was planning on doing a disk image, and then mounting it in linux to do all of my work.

---

### Post by aks44 on 2007-11-19
> **intelligentfool said:**
> I was told this app is running on a Win95 machine.

That thing being 10yo it's hard to tell for sure if it was "bleeding edge" (Win32/PE) technology, or just plain old Win16/MZ.

Anyway, if the Win32 "dependency viewer" SDK tool can't read it, it is definitely a 16-bit thingie.
But I really hope (for you) it's a Win32 application, they are *way* easier to debug...

---

### Post by intelligentfool on 2007-11-19
probably a dumb question, but what do "PE" and "MZ" stand for?

---

### Post by aks44 on 2007-11-19
PE = "Portable Executable", aka. the specification of Win32 (and Win64??) binaries (both .exe programs and .dll libraries), first introduced with Windows NT. The PE format (although not individual PE files) is portable across the different architectures that Windows is able to run on.

MZ = the good old DOS (16-bit) .exe binary format. Those are the first two bytes of such files, originating from *Mark Zbikowski* (a Microsoft developer) who designed the format.

---

### Post by j_g on 2007-11-20
Damn you, aks44. You rushed in here and told him everything I was going to say (without needing the OP to be more coherent too!).

I second every bit of this advice. I've personally used IDA to reverse engineer some stuff, and it's great. It resolves a lot of system calls and C library calls for you. For example, it will load up the exe and wherever the exe makes a call to some Win32 API such as CreateFile, WriteFile, CloseFile, it will put that function call right there in the disassembly. Same too if the exe calls fopen(), fwrite(), fclose(), strcpy(), malloc(), etc. So that could help you zero in on the part of the exe you need to examine -- the file calls. (But you still need to be able to read an Intel assembly listing). It also automatically detects ascii strings in the data section, and will show them as so. So, you may see this sort of thing shown (actual output of IDA, on a file I'm currently reverse-engineering... um, you didn't see this):

```
aCanTQueryMediaType db 'Can',27h,'t query media type: ',0
```

Then it substitutes the label aCanTQueryMediaType wherever it's referenced in the code listing.

I never tried it upon an older EXE format, but it does support formats going back to MS-DOS, so should work on those too. Get the company to buy it for you, if needed.

One caution. Make a copy of the EXE you intend to diassemble. IDA sometimes "reformats" the EXE when it disassembles it, and subsequently Windows will report that copy of the EXE as a mal-formed EXE when you try to run it. So, work upon a backup copy.

But, aks's advice about reverse-engineering one of the data files is spot on too. I'd start with this approach first, especially if the data file is small, or you're not adept at Intel asm. Start with an empty file. (ie, All settings in the EXE at default values). Load it into a "hex editor" (such as HexEdit, but there's lots of them, including free ones). Leave that file loaded. Now make one change to only one parameter (using the EXE you're reverse-engineering). Save _a second_ data file. Load that second file into the hex editor as well (so both files are loaded). Then, tell the hex editor to do a comparison and highlight the difference. (Use a hex editor that has this feature). You'll likely see one or more bytes highlighted. Note the byte offset from the start of the file, to the changed byte(s), and what the change is. Keep written notes. Reload the empty data file in the EXE being reverse-engineered. Now make one change to some other setting. Resave to that second file, load it in the hex editor, and compare it to the empty file. Repeat with other settings. Eventually you'll get a good idea of what settings are stored where in the data file.

In before a moderator may lock the thread. (It's not about the evil history of MS).

---

