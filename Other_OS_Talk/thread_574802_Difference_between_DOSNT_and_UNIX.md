---
title: "Difference between DOS/NT and UNIX?"
date: 2007-10-13
forum: Other OS Talk
---

### Post by Martial-law on 2007-10-13
What is the difference between DOS and UNIX? I have tried a lot of searching but could not an appropriate answer. As far as I know Windows is based on DOS and Linux, BSD, Mac and Solaris on UNIX. And the latest versions of Windows are not based on DOS but NT which is "New Technology". Both DOS and UNIX are languages upon which the operating systems are built. Thus both should be equal in terms of effeciency, security and stability. So why people always blame the Windows OS for the lack of effeciency, security and stability when the developers of a similar OS React also say that "Operating systems based on DOS/NT are not inherently unstable and insecure". 90% of world desktops are running on DOS/NT based systems, isn't that proof that DOS is a successful language? Also I would like to know as to why there are so many operating systems based on UNIX and just two on DOS/NT? Anyone knowing the history may guide please. And also are there just two languages throughout the world i.e. DOS/NT and UNIX upon which Operating systems could be built or are there some more? Too many questions in just a single post sorry for that but I am very curious to know about this matter and hope some geek would inform me about all this. Thanks in advance.:)

---

### Post by kvonb on 2007-10-13
DOS and Unix are not languages, they are Operating Systems.

DOS = Disk Operating System, the true term is Microsoft Disk Operating System if you are referring to the Microsoft product.

A piece of software that controls and manages all the devices inside the computer.

And there are many thousands of examples of things in the world that are more in use than others, not because they are better, but simply because of political/religious/economic/advertising factors.

It is a common misconception that William Gates created the MSDOS, he simpy purchased it from an unsuspecting stooge who did all the hard work.

MSDOS is a single task, single user system, and is designed to run only on the machine it is installed on.  Unix is a multi user, multi-task system which was designed to be used non-centrally, ie over a network.

Unix doesn't see a "computer", it sees a series of connections to devices.  MSDOS sees only the local computer.

They are chalk and cheese!

Oh and NT is not that different from the old MSDOS/Windows setup, they simply shuffled things around a bit.  Same old, same old.

---

### Post by the_darkside_986 on 2007-10-13
I think NT is MS attempt at implementing some Unix features in their OS such as multi-users, for example. But it fails miserably because I can never get anything to run without admin privileges and and the RunAs command doesn't seem to work in Vista :(

Of course, NT is certainly a major improvement over MSDOS and Win9x, at least for security. Someone told me they considered putting '98 back on their laptop and I told them they might as well purposefully install lots of random malware since that is the effect of having an old Win9* machine on the internet for 3 seconds with internet explorer 6.

---

### Post by fistfullofroses on 2007-10-14
MSDOS is based upon CP/M, and was not made by Microsoft at all. It was bought from a small computer company, Seattle Computer Products (where it had been made by by Tim Paterson). Also, there are many versions of DOS. QDOS, MSDOS, DR DOS, PCDOS, FreeDOS, GNU/DOS, OpenDOS, PTS-DOS, Novell DOS, OS/2, and NT. 

Your mention of NT did not go unnoticed, btw. I think it is unfortunate that people do not realize where NT comes from and what it is. In the late 80s Microsoft had already ditched their Unix operating system, Xenix. They declared boldly that DOS was dead and promoted OS/2. OS/2 was a merger of DOS and Xenix. Though Microsoft would continue to use Xenix within their own company for quite some time, they no longer promoted it. When OS/2 fell flat on its face, They began this long Windows saga, using bits and pieces of OS/2 in NT.

---

### Post by kellemes on 2007-10-14
Previous posters just about explain it..
But to confuse the DOS-matter some more.. the first DOS I touched in my life happens to be [Apple DOS]("http://en.wikipedia.org/wiki/Apple_DOS")

---

### Post by 3rdalbum on 2007-10-16
I was just about to mention that: DOS is not the underlying layer of any Microsoft operating system. MS-DOS is the underlying layer. Big difference. But if DOS was the underlying layer of Windows, the situation wouldn't be improved any :-)

---

### Post by ezsit on 2007-10-16
> OS/2 was a merger of DOS and Xenix. Though Microsoft would continue to use Xenix within their own company for quite some time, they no longer promoted it. When OS/2 fell flat on its face, They began this long Windows saga, using bits and pieces of OS/2 in NT.

OS/2 was nothing like MS-DOS. OS/2 was a multi-threaded, multi-tasking, single-user operating system with an advanced filesystem and graphical user interface. OS/2 provided virtual DOS sessions and compatibility, but the underlying OS was a very robust design.

OS/2 was not based on Unix code and bore little resemblence to Unix.

OS/2 versions 1.0 through 1.3 were developed jointly by IBM and Microsoft as the replacement for DOS. However, around 1990, Windows started to sell well and Microsoft decided to focus on that instead of OS/2. IBM took over total development of OS/2 and released version 2 with a new GUI called the workplace shell. The old GUI was a copy of the Windows 2.11 interface.

Windows NT was originally started as OS/2 version 3, but when Microsoft and IBM split, Microsoft hired David Cutler from Digital Equipment Corp. (DEC) and Cutler oversaw the rewritting of Windows NT as a microkernel replacement for Unix that MS could compete in the server and corporate market.

---

