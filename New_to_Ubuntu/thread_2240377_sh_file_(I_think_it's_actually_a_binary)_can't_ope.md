---
title: "sh file (I think it's actually a binary) can't open xterm"
date: 2014-08-19
forum: New to Ubuntu
---

### Post by dave131 on 2014-08-19
Newbie here.

Trying to help a user get their lexmark printer working in Ubuntu.  Found the appropriate linux driver at lexmark and downloaded it, uncompressed it and ran the sh file as the instructions said.  At first it didn't work because it was looking for bin/linux/x86/libc.so.6, so I tried creating a folder in the Downloads folder of bin/lib/x86 and created a link there to the 64-bit libc.so.6 (I thought it would at least get past this problem but give me errors as it tried to actuall use the library) - didn't work.  Tried the same but in /bin - didn't work.  Backed out both attempts so the folders were cleaned up.

Opened synaptic package manager and found the package for g++ for i386 - clicked it for install and it included 2 other packages (I think 1 of those was the actual i386 support libraries).  I then ran the script again and got past the initial error.  I know that this is supposed to eventually open a gui to install/config the printer, but I now get an error that it can't open xterm, so I don't know if there is another (older) version I might need as the last update I can find on the net for actually installing this was back in 10.xx.   The attachment is a screen capture.

---

### Post by ubudog on 2014-08-19
Welcome!

See if xterm can be installed:
```
sudo apt-get install xterm
```

---

### Post by dave131 on 2014-08-19
It's says xterm is already installed and current.  I can open a terminal, type xterm and press enter and it does open a xterm terminal window.

I'm wondering if the paths have changed since 10.xx, or perhaps even how X11 is referred to, such that I might need to create some kind of "dummy" folders fold X11 paths and link them to the current paths, including executables as needed.  I have a hunch the program is referring to xterm via a full path.

Thanks for the reply and help!

---

### Post by ubudog on 2014-08-19
Hmm, what does:
```
cat lexmark-08z-series-driver-1.0-1.i386.deb.sh | grep -i xterm
```
give you?

---

### Post by dave131 on 2014-08-19
I only get this:

```
me@me1735:~/Downloads$ cat lexmark-08z-series-driver-1.0-1.i386.deb.sh | grep -i xterm
Binary file (standard input) matches
me@me1735:~/Downloads$ 
```

Kind of weird that it can't open xterm yet the actual word xterm is not in the file.  I wonder if it's trying to use something and in turn that "something" requires xterm. 

I did try opening terminal, typing xterm and pressing enter, then going to the xterm window and running the sh file as well and still get the same error.

Since this appears to be a binary executable, and there is no source code, do you know if there is any way to trace what X calls are being made - like some sort of X trace?  Seems to me like I used something like that years ago but don't remember what it was or how it works.

Thanks again.

---

### Post by dave131 on 2014-08-19
I was just looking at another thread on the net about a similar problem and tried something it mentioned there:

- opened a terminal via ctrl/alt/F6 and logged in
- went to Downloads and ran it the same as before and now get this at the end instead of xterm:
[code]Error opening terminal: linux[code]

I also noticed that when I use that same terminal and type xterm I get errors, starting with DISPLAY not being defined.

When I have been doing this before, including typing in xterm and it worked, it was via the "Terminal" launcher in the menu. 

Perhaps this helps - perhaps it just muddies things up more ;)

---

### Post by steeldriver on 2014-08-19
I wouldn't expect running from one of the Ctrl-Alt-Fn virtual terminals to work - unless it's smart enough to figure out that there is no X session and run in some kind of text-based mode

FYI the word 'xterm' is there - as indicated by the grep message "Binary file (standard input) matches" - but you need to be a bit more devious to see it e.g.

```

$ **strings** lexmark-08z-series-driver-1.0-1.i386.deb.sh | **grep 'xterm'**
  --nox11               Do not spawn an xterm
xterm_loop=
    xterm_loop=1
        if test x"$DISPLAY" != x -a x"$xterm_loop" = x; then  # No, but do we have X?
                GUESS_XTERMS="xterm rxvt dtterm eterm Eterm kvt konsole aterm"

```

I don't have a Lexmark printer but I was able to run the extracted 32-bit sh file on my 32-bit 12.04 system and it popped up a graphical installer window - it didn't seem to be using xterm as far as I could tell though (using ps). FWIW I also tried adding the --nox11 option mentioned in the 'strings' output, but it didn't seem to make any difference (the GUI installer window still popped up).

Since it's trying to open a GUI app you may have better luck using gksudo (or gksu) instead of plain sudo since that handles the GUI environment better. 


Sorry I can't help more

---

### Post by ubudog on 2014-08-19
Big +1 to steeldriver's post.

It might also be useful to know what $TERM is:
```
echo $TERM
```

---

### Post by dave131 on 2014-08-19
Ok - found another link with some info that at least got me to the gui:

- had to link /lib/terminfo and /usr/share/terminfo

This then allowed the gui to come up and I could go through the setup until I accepted the license agreement and it started installing - I get an error in the actual install process itself that goes too quick to catch but the gui itself doesn't error out - it keeps running and says the install did not complete. 

So, a BIG step in the right direction.  

Any idea how to copy outputs from a xterm window to a file so I can see them?

Thanks.

---

### Post by dave131 on 2014-08-19
It goes by so dang quick and then gets mostly covered by the error message window the program pops up.  It looks like something with dpkg, but I just can't catch it.

In the opening text where it shows requirements, it says it's 32-bit only and the only ubuntu release supported is 9.10 - even though I saw reference to this with ubuntu 10.xx on the net.

Does dpkg keep some sort of error log somewhere?

---

### Post by ubudog on 2014-08-19
It's probably a dependency issue, but we will see:
```
cat /var/log/dpkg.log
```

---

### Post by dave131 on 2014-08-19
Another step forward?  When the installer showed the error box, instead of pressing ok I instead looked in /tmp and found a folder there it had created.  I copied that folder to my folder and changed ownership, etc., on it.  Then I pressed ok on the error box.  That way I kept a copy of the files it creates which are the actual installation files.  I tried installing the driver, and it starts up in the software center.  I select install - it gives a warning about basically not being up to standards or some such thing, then continues for a while before it says error in the file/archive and stops the installation.

Right now I'm a little lost at what else to try.  I'll keep plugging along in that folder and see if I can figure anything out.

---

### Post by dave131 on 2014-08-19
> **ubudog said:**
> It's probably a dependency issue, but we will see:
```
cat /var/log/dpkg.log
```

I did try that previous to my last post but there was nothing in it for the installation, only for things I had installed earlier.

Thanks.

---

### Post by dave131 on 2014-08-19
> **steeldriver said:**
> I wouldn't expect running from one of the Ctrl-Alt-Fn virtual terminals to work - unless it's smart enough to figure out that there is no X session and run in some kind of text-based mode

FYI the word 'xterm' is there - as indicated by the grep message "Binary file (standard input) matches" - but you need to be a bit more devious to see it e.g.

```

$ **strings** lexmark-08z-series-driver-1.0-1.i386.deb.sh | **grep 'xterm'**
  --nox11               Do not spawn an xterm
xterm_loop=
    xterm_loop=1
        if test x"$DISPLAY" != x -a x"$xterm_loop" = x; then  # No, but do we have X?
                GUESS_XTERMS="xterm rxvt dtterm eterm Eterm kvt konsole aterm"

```

I don't have a Lexmark printer but I was able to run the extracted 32-bit sh file on my 32-bit 12.04 system and it popped up a graphical installer window - it didn't seem to be using xterm as far as I could tell though (using ps). FWIW I also tried adding the --nox11 option mentioned in the 'strings' output, but it didn't seem to make any difference (the GUI installer window still popped up).

Since it's trying to open a GUI app you may have better luck using gksudo (or gksu) instead of plain sudo since that handles the GUI environment better. 


Sorry I can't help more

I missed your post - sorry.   I did get the gui to come up but it comes up with an error and doesn't install the driver.  Are you willing to go through the installation from the gui screen to see if you get any error?

Thanks.

---

### Post by steeldriver on 2014-08-19
I did - it errored out for me as well. 

```

gksudo lexmark-08z-series-driver-1.0-1.i386.deb.sh

```

I captured the error output from the GUI window (Ctrl-A Ctrl-C):

```

Extracting file: printdriver.te
Extracting file: lexmark-08z-series-driver-1.0-1.i386.deb
Extracting file: launcher.c
Extracting file: launcher
Extracting file: lsbrowser
Extracting file: lsusbdevice
Using dpkg installation
=============================
Execute: dpkg -i --force-architecture lexmark-08z-series-driver-1.0-1.i386.deb > /tmp/selfgz21250/pkg/files/dpkg_msgs

dpkg: error processing lexmark-08z-series-driver-1.0-1.i386.deb (--install):
 parsing file '/var/lib/dpkg/tmp.ci/control' near line 9 package 'lexmark-08z-series-driver':
 blank line in value of field 'Description'
Errors were encountered while processing:
 lexmark-08z-series-driver-1.0-1.i386.deb
=============================

=============================
Execute: rm lexmark-08z-series-driver-1.0-1.i386.deb

=============================
***** ERROR REPORT *****

```

FWIW I also captured the screen before the license agreement screen, which seems to indicate that the package is for Ubuntu 9.10, so I'm not really surprised it fails

```

===================================
Lexmark 08z Series Driver README
===================================

1. Minimum System Requirements:
-------------------------------
500 MHz Processor Speed
256 MB RAM
300 MB free Hard Disk Space

2. Supported Operating Systems:
-------------------------------
  openSUSE 11.2
  Ubuntu 9.10
  Fedora 12

  Note: 32-bit support only.

3. Supported Language:
-----------------------
  English Only

4. Licenses Notices:
--------------------
The printer resident software contains software developed
and copyrighted by Lexmark.

In addition, the printer resident software may
contain:
 * Lexmark modified software licensed under the provisions of the GNU
    General Public License version 2
 * Software licensed under other licenses

The following documents may be viewed at the bottom of this readme.txt
file:
 * GNU General Public License version 2

The Lexmark modified third-party software covered by this third-party
license is free software; you can redistribute it and/or modify it
under the terms of the license referenced above.  This license does not
provide you any rights to the Lexmark copyrighted software in this
printer.

Since the third-party licensed software that the Lexmark modifications
are based on is supplied explicitly without warranty, use of the Lexmark
modified version is similarly provided without warranty.  See the
warranty disclaimers in the referenced licenses for additional details.

To obtain source code files and source code
information required to be made available with the product, see the Open
Source section below.

5. Installation:
----------------
 1. Do not attach the printer via USB to the Linux machine.
 2. Extract the zip file.
     For RPM-based systems: lexmark-08z-series-driver-1.0-1.i386.rpm.sh.tar.gz
     For DEB-based systems: lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz
 3. Run the installer script file by double-clicking on the file icon and
    then click the "Run in Terminal" button or run the script file via command-line.
 4. Follow the instructions in the installer screen.

6. Manually adding the Printer in CUPS:
---------------------------------------
 1. Attach the printer via USB to the Linux machine.
 2. Run a browser and open "http://localhost:631"
 3. Click "Add Printer" and fill out the details, such as name and description.
    In the Device dropdown list, select "Lexmark <printer model> USB #1"
    Make sure you select the correct device. The printer is not detected by the
    machine if you cannot see its model in the list. On some distro, you may have
    to reboot the machine so it can be detected.

    You can also Browse for the PPD file if the device is not on the list.
    The ppd files are located in folder /usr/lexinkjet/08zero/etc/. The following
    are the different models supported by this driver and with their matching
    ppd file:

    Printer                            PPD
    ------------------------------------------------------
    Lexmark Z2400 Series         ..... lxZ2400.ppd
    Lexmark 3600-4600 Series     ..... lx36-46.ppd
    Lexmark 4900 Series          ..... lx4900.ppd
    Lexmark 5600-6600 Series     ..... lx56-66.ppd
    Lexmark 7600 Series          ..... lx7600.ppd

7. Uninstallation:
------------------
  For Debian-based package:
   1. Login as root.
   2. Uninstall the DEB package: dpkg -r <package>
        e.g. #dpkg -r lexmark-08z-series-driver

  For RPM-based package:
   1. Login as root.
   2. Uninstall the RPM package: rpm -e <package>,
        e.g. #rpm -e lexmark-08z-series-driver

8. Open Source:
---------------
   1. The open source Nixstaller was used in creating the installer for this driver.
      Nixstaller is licensed under the GNU General Public License version 2. To obtain
      a copy of this license see the Licenses Notices above.

      To obtain the source code contact Lexmark at Lexmark Technical Support or go to
      the Nixstaller website at http://nixstaller.berlios.de/downloads.php.

      To obtain source code files for the Lexmark modified GNU licensed software, contact
      Lexmark Technical Support.

   2. The open source Common UNIX Printing System (tm), ("CUPS (tm)") used in this driver is licensed
      under the GNU General Public License version 2.  To obtain a copy of this license see the
      Licenses Notices above.

      To obtain source code files for the Lexmark modified CUPS licensed software, contact
      Lexmark Technical Support.

9. Frequently Asked Questions:
------------------------------
         

                  GNU GENERAL PUBLIC LICENSE
                       Version 2, June 1991

Copyright (C) 1989, 1991 Free Software Foundation, Inc.
59 Temple Place, Suite 330, Boston, MA  02111-1307 USA

Everyone is permitted to copy and distribute verbatim copies of this
license document, but changing it is not allowed.

                       Preamble

  The licenses for most software are designed to take away your freedom to
share and change it. By contrast, the GNU General Public License is intended
to guarantee your freedom to share and change free software--to make sure the
software is free for all its users.  This General Public License applies to
most of the Free Software Foundation's software and to any other program
whose authors commit to using it.  (Some other Free Software Foundation
software is covered by the GNU Library General Public License instead.)
You can apply it to your programs, too.

  When we speak of free software, we are referring to freedom, not price.
Our General Public Licenses are designed to make sure that you have the freedom
to distribute copies of free software (and charge for this service if you wish),
that you receive source code or can get it if you want it, that you can change
the software or use pieces of it in new free programs; and that you know you
can do these things.

  To protect, your rights, we need to make restrictions that forbid anyone to
deny you these rights or to ask you to surrender the rights. These restrictions
translate to certain responsibilities for you if you distribute copies of the
software, or if you modify it.

  For example, if you distribute copies of such a program, whether gratis or for
a fee, you must give the recipients all the rights that you have.  You must make
sure that they, too, receive or can get the source code.  And you must show them
these terms so they know their rights.

  We protect your rights with two steps: (1) copyright the software, and
(2) offer you this license which gives you legal permission to copy, distribute
and/or modify the software.

  Also, for each author's protection and ours, we want to make certain everyone
understands that, there is no warranty for this free software.  If the
software is modified by someone else and passed on, we want its recipients to
know that what they have is not the original, so that any problems introduced
by others will not reflect on the original authors' reputations.

  Finally, any free program is threatened constantly by software patents.  We
wish to avoid the danger that redistributors of a free program will individually
obtain patent licenses, in effect making the program proprietary.  To prevent
this, we have made it clear that any patent must be licensed for everyone's free
use or not licensed at all.

The precise terms and conditions for copying, distribution and modification follow.


               GNU GENERAL PUBLIC LICENSE
            TERMS AND CONDITIONS FOR COPYING, 
              DISTRIBUTION AND MODIFICATION

 0. This License applies to any program or other work which contains a notice
placed by the copyright holder saying it may be distributed under the terms of
this General Public License. The "Program", below, refers to any such program or
work, and a "work based on the Program" means either the Program or any derivative
work under copyright law: that is to say, a work containing the Program or a
portion of it, either verbatim or with modifications and/or translated into
another language.  (Hereinafter, translation is included without limitation in
the term "modification".)  Each licensee is addressed as "you".

Activities other than copying, distribution and modification are not covered by
this License; they are outside its scope.  The act of running the Program is not
restricted, and the output from the Program is covered only if its contents
constitute a work based on the Program (independent of having been made by running
the Program). Whether that is true depends on what the Program does.

  1. You may copy and distribute verbatim copies of the Program's source code as
you receive it, in any medium, provided that you conspicuously and appropriately
publish on each copy an appropriate copyright notice and disclaimer of
warranty: keep intact all the notices that refer to this License and to the
absence of any warranty; and give any other recipients of the Program a copy
of this License along with the Program.

You may charge a fee for the physical act of transferring a copy, and you may at
your option offer warranty protection in exchange for a fee.

  2. You may modify your copy or copies of the Program or any portion of it, thus
forming a work based on the Program, and copy and distribute such modifications
or work under the terms of Section 1 above, provided that you also meet all of
these conditions:

    a) You must cause the modified files to carry prominent notices stating that
    you changed the files and the date of any change.

    b) You must cause any work that you distribute or publish, that in whole or in
    part contains or is derived from the Program or any part thereof, to be licensed
    as a whole at no charge to all third parties under the terms of this License.

    c) If the modified program normally reads commands interactively when run, you
    must cause it, when started running for such interactive use in the most ordinary
    way, to print or display an announcement including an appropriate copyright
    notice and a notice that there is no warranty (or else, saying that you provide a
    warranty) and that users may redistribute the program under these conditions,
    and telling the user how to view a copy of this License.  (Exception: if the
    Program itself is interactive but does not. normally print such an announcement,
    your work based on the Program is not required to print an announcement.)

These requirements apply to the modified work as a whole.  If identifiable sections
of that work are not derived from the Program, and can be reasonably
considered independent and separate works in themselves, then this License,
and its terms, do not apply to those sections when you distribute them as
separate works. But when you distribute the same sections as part of a whole
which is a work based on the Program, the distribution of the whole must be on
the terms of this License, whose permissions for other licensees extend to the
entire whole, and thus to each and every part regardless of who wrote it.

Thus, it is not the intent of this section to claim rights or contest your
rights to work written entirely by you; rather, the intent is to exercise the
right to control the distribution of derivative or collective works based on
the Program.

In addition, mere aggregation of another work not based on the Program with the
Program (or with a work based on the Program) on a volume of a storage or distribution
medium does not bring the other work under the scope of this License.

  3. You may copy and distribute the Program (or a work based on it, under Section 2)
in object code or executable form under the terms of Sections 1 and 2 above provided
that you also do one of the following:

    a} Accompany it with the complete corresponding machine-readable source code,
    which must be distributed under the terms of Sections 1 and 2 above on a
    medium customarily used for software interchange; or,

    b) Accompany it with a written offer, valid for at least three years, to give
    any third party, for a charge no more than your cost of physically performing
    source distribution, a complete machine-readable copy of the corresponding source
    code, to be distributed under the terms of Sections 1 and 2 above on a medium
    customarily used for software interchange; or,

    c) Accompany it with the information you received as to the offer to distribute
    corresponding source code,   (This alternative is allowed only for noncommercial
    distribution and only if you received the program in object code or executable
    form with such an offer, in accord with Subsection b above.)

The source code for a work means the preferred form of the work for making modifications
to it.  For an executable work, complete source codes means all the source code for all
modules it contains, plus any associated interface definition files, plus the scripts
used to control compilation and installation of the executable.  However, as a
special exception, the source code distributed need not include anything that,
is normally distributed (in either source or binary form) with the major
components (compiler, kernel, and so on) of the operating system on which the
executable runs, unless that component itself accompanies the executable.

If distribution of executable or object code is made by offering access to copy
from a designated place, then offering equivalent access to copy the source
code from the same place counts as distribution of the source code, even
though third parties are not compelled to copy the source along with the
object code.

  4. You may not copy, modify, sublicense, or distribute the Program except, as expressly
provided under this License.  Any attempt otherwise to copy, modify, sublicense or
distribute the Program is void, and will automatically terminate your rights under this
License.  However, parties who have received copies, or rights, from you under this
License will not have their licenses terminated so long as such parties remain in full
compliance.

  5. You are not required to accept this License, since you have not signed it.
However, nothing else grants you permission to modify or distribute the
program or its derivative works. These actions are prohibited by law if you do
not accept this License.  Therefore, by modifying or distributing the Program
(or any work based on the Program), you indicate your acceptance of this
License to do so, and all its terms and conditions for copying, distributing
or modifying the Program or works based on it.

  6. Each time you redistribute Program (or any work based on the Program), the recipient
automatically receives a license from the original licensor to copy, distribute or modify
the Program subject to these terms and conditions.  You may not impose any further
restrictions on the recipients' exercise of the rights granted herein. You are not
responsible for enforcing compliance by third parties to this License.

  7. If, as a consequence of a court judgment or allegation of patent infringement or for
any other reason (not limited to patent issues), conditions are imposed on you (whether
by court order, agreement or otherwise) that contradict the conditions of this License,
they do not excuse you from the conditions of this License.  If you cannot distribute so
as to satisfy simultaneously your obligations under this License and any other pertinent
obligations, then as a consequence you may not distribute the Program at all. For example,
if a patent license would not permit royalty-free redistribution of the Program by all
those who receive copies directly or indirectly through you, then the only way you could
satisfy both it and this License would be to refrain entirely from distribution or the
Program.

If any portion of this section is held invalid or unenforceable under any particular
circumstance, the balance of the section is intended to apply and the section as a whole
is intended to apply in other circumstances. It is not the purpose of this section to
induce you to infringe any patents or other property right claims or to contest validity
of any such claims; this section has the sole purpose of protecting the integrity of the
free software distribution system, which is implemented by public license practices.
Many people have made generous contributions to the wide range of software distributed
through that system in reliance on consistent application of that system; it is up to the
author/donor to decide if he or she is willing to distribute software through
any other system and a licensee cannot impose that choice.

This section is intended to make thoroughly clear what is believed to be a consequence of
the rest of this License.

  8. If the distribution and/or use of the Program is restricted in certain countries
either by patents or by copyrighted interfaces, the original copyright holder who places
the Program under this License may add an explicit geographical distribution limitation
excluding those countries, so that  distribution is permitted only in or among countries
not thus excluded.  In such case, this License incorporates the limitation as
if written in the body of this License.

  9. The Free Software Foundation may publish revised and/or new versions of the General
Public License from time to time.  Such new versions will be similar in spirit to the
present version, but may differ in detail to address new problems or concerns.

Each version is given a distinguishing version number.  If the Program specifies a version
number of this License which applies to it and "any later version", you have the option of
following the terms and conditions either of that version or of any later version
published by the Free Software Foundation.  If the Program does not specify a version
number of this License, you may choose any version ever published by the Free Software
Foundation.

  10. If you wish to incorporate parts of the Program into other free programs whose
distribution conditions are different, write to the author to ask for permission.
For software which is copyrighted by the Free Software Foundation, write to the Free
Software Foundation; we sometimes make exceptions for this.  Our decision will be
guided by the two goals of preserving the free status of all derivatives of
our free software and of promoting the sharing and reuse of software
generally.

              NO WARRANTY

  11. BECAUSE THE PROGRAM IS LICENSED FREE OF CHARGE, THERE IS NO WARRANTY FOR THE PROGRAM,
TO THE EXTENT PERMITTED BY APPLICABLE LAW.  EXCEPT WHEN OTHERWISE STATED IN WRITING THE
COPYRIGHT HOLDERS AND/OR OTHER PARTIES PROVIDE THE PROGRAM "AS IS" WITHOUT WARRANTY OF ANY
KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF
MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE.  THE ENTIRE RISK AS TO THE QUALITY
AMD PERFORMANCE OF THE PROGRAM IS WITH YOU.  SHOULD THE PROGRAM PROVE DEFECTIVE, YOU ASSUME
THE COST OF ALL NECESSARY SERVICING, REPAIR OR CORRECTION.

  12. IN NO EVENT UNLESS REQUIRED BY APPLICABLE LAW OR AGREED TO IN WRITING WILL ANY
COPYRIGHT HOLDER, OR ANY OTHER PARTY WHO MAY MODIFY AND/OR REDISTRIBUTE THE PROGRAM AS
PERMITTED ABOVE, BE LIABLE TO YOU FOR DAMAGES, INCLUDING ANY GENERAL, SPECIAL, INCIDENTAL
OR CONSEQUENTIAL DAMAGES ARISING OUT OF THE USE OR INABILITY TO USE THE PROGRAM (INCLUDING
BUT NOT LIMITED TO LOSS OF DATA OR DATA BEING RENDERED INACCURATE OR LOSSES SUSTAINED BY
YOU OR THIRD PARTIES OR A FAILURE OF THE PROGRAM TO OPERATE WITH ANY OTHER PROGRAMS),
EVEN IF SUCH HOLDER OR OTHER PARTY HAS BEEN ADVISED OF THE POSSIBILITY OF SUCH DAMAGES.

              END OF TERMS AND CONDITIONS

         How to Apply These Terms to Your New Programs

  If you develop a new program, and you want It to be of the greatest possible use to the
public, the best way to achieve this is to make it free software which everyone can
redistribute and change under these terms.

  To do so, attach the following notices to the    program.  It is safest to attach them to
the start of each source file to most effectively convey the exclusion of warranty; and
each file should have at least the "copyright" line and a pointer to where the full
notice is found.

    <one line to give the program's name and a brief idea of what it does.>
    Copyright (C) 19yy  <name of author>

    This program is free software; you can redistribute it and/or modify it
    under the terms of the GNU General Public License as published by the Free
    Software Foundation; either version 2 of the License, or (at your option)
    any later version.

    This program is distributed in the hope that it will be useful, but WITHOUT
    ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or
    FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for
    more details.

    You should have received a copy of the GNU General Public License along
    with this program; if not, write to the Free Software Foundation, Inc., 59
    Temple Place, Suite 330, Boston, MA 02111-1307  USA

Also add information on how to contact you by electronic and paper mail.

If the program is interactive, make it output a short, notice like this when it starts in an
interactive mode:

    Gnomovision version 69, Copyright (C) 19yy name of author
    Gnomovision comes with ABSOLUTELY NO WARRANTY; for details type `show W'.
    This is free software, and you are welcome to redistribute it under certain
    conditions; type 'show c' for details.

The hypothetical commands 'show w' and `show c' should show the appropriate parts of the
General Public License. Of course, the commands you use may be called something other than
`show w' and `show c'; they could even be mouse-clicks or menu items--whatever suits
your program.

You should also get your employer (if you work as a programmer) or your school, if any, to
sign a "copyright disclaimer" for the program, if necessary.  Here is a sample; alter the
names:

    Yoyodyne, Inc., hereby disclaims all copyright interest in the program 
    'Gnomovision' (which makes passes at compilers) written by James Hacker.

    <signature of Ty Coon>, 1 April 1989
    Ty Coon, President of Vice

This General Public License does not permit incorporating your program into proprietary
programs.  If your program is a subroutine library, you may consider it more useful to
permit linking proprietary applications with the library.  If this is what you want to do,
use the GNU Library General Public License instead of this License.

```

---

### Post by dave131 on 2014-08-19
Thanks for all of that.  I noticed the 9.xx version as well, and had seen posts on the net for version 10.  I was just really hoping it would work so I could try to help the user out - kind of the first big help if I could be.  Oh well.  I can't find anything else for lexmark drivers anywhere either.  Lexmark never made the source code available from the best I could tell so there's apparently no way to rebuild it in the current ubuntu.  Guess I'll keep looking! 

Thanks everyone.

---

### Post by steeldriver on 2014-08-19
I did a bit more digging around and found this --> [http://downloads.lexmark.com/downloads/pssd/print-drivers-linux-glibc2-x86.deb](http://downloads.lexmark.com/downloads/pssd/print-drivers-linux-glibc2-x86.deb)

I have no idea if the package includes drivers for your printer, but it does seem to install OK on my 32-bit 12.04 box. It's a plain deb file not a shell archive:

```

$ sudo dpkg -i print-drivers-linux-glibc2-x86.deb 
Selecting previously unselected package drivers-lexprtdrv.
(Reading database ... 464533 files and directories currently installed.)
Unpacking drivers-lexprtdrv (from .../print-drivers-linux-glibc2-x86.deb) ...

--------------------------
Installing LEXPrtDrv ...
--------------------------
Please remember to review the license agreement before
using this software.
Setting up drivers-lexprtdrv (5.6.1-2) ...
Debian GNU/Linux Distribution.

EU waste electronics information
********************************

The WEEE logo signifies specific recycling programs and procedures for 
electronic products in countries of the European Union. We encourage 
the recycling of our products. If you have further questions about 
recycling options in European Union countries, please refer to the 
document listed below.

  /usr/local/lexmark/docs/EU_Waste_Electronic_Information.pdf

*******************************


Lexmark Print Drivers is installed.

You must run the following script to complete the installation.

   # /usr/local/lexmark/setup.lexprint 

   -- Updating symbolic links

```

```

$ sudo /usr/local/lexmark/setup.lexprint
---------------------------------------------------
Lexmark Print Drivers Setup Script
---------------------------------------------------

This application is a suid root program, which allows the
root user or members of the administrative group to have
administrative privileges. These privileges include adding,
removing, and modifying printer queues.

To set the administrative group, select any valid group.
The default is ( bin ).

Enter an administrative group ( bin ): lpadmin
---------------------------------------------------

Lexmark Print Drivers Help System consists of html files.
To be able to view these html help files, we need the
absolute path to a valid "Web Browser".

1. /usr/bin/firefox
2. Specify a web browser.
3. None.

Enter your choice : [3] 
---------------------------------------------------
Default paper size selection.

 1.  Letter (default)
 2.  A4

Enter your choice : [1] 
---------------------------------------------------
Asian Driver Support

Enabling Asian Driver support provides users with additional Asian
printing options, such as printing with and without the Asian Font
DIMM.  You can access these features from the driver properties
font tab.

In-order to take advantage of these features, you must enable this
option and create a printer queue with Asian in the model name.

Do you want to enable Asian driver support?

 1.  Disable (default)
 2.  Enable

Enter your choice : [1] 
---------------------------------------------------

Lexmark Menu Utility

  1. Install Lexmark applications.
  2. Remove Lexmark applications.
  3. Exit.

Enter your choice : [3] 

---------------------------------------------------
Enabling CUPS print support
---------------------------------------------------
Debian GNU/Linux Distribution.
---------------------------------------------------
Setup complete!

```

---

### Post by 1clue on 2014-08-19
This is speculation, but what you're experiencing sounds like my absolutely least favorite way of packaging an app.  In fact, I'd add a few notches of honorary unpleasantness below my next least favorite, which is to buy Microsoft software from some "value added reseller" which means it's infested with malware already.

I suspect this is a shell script with an encoded binary in it.  Basically they hardcode data in a format that makes sense to bash but is insensitive to line endings or other text file gotchas.

To install the package, you do this as root:
```

. ./myShellScript.sh

```

Note the "." at the front.  This invokes a shell in the current environment with the current permissions, writes the data to a file (or many files), and then installs the file.

I hope i'm wrong.  In my experience this mechanism works moderately well if the software is installed shortly after it was packaged, and never again after any significant update.

---

### Post by dave131 on 2014-08-19
Steeldriver:  thanks for the link.  I checked the description details for it and unfortunately it doesn't include the users' printer.

1clue:  doesn't do anygood.  I found another post on the net that shows how to actually extract the files, then build the deb again - supposedly to get 64-bit support since I'm on a system that is 64-bit.

The error appears to be that the headers themselves in the deb are screwed up.  I followed the instructions to rebuild it, but it appears to use a binary file (I can't edit it) that tells tar what to do - and the resulting deb file still has those errors.

Since there is no source available, I appreciate any help I can get.  The user who posted in the forums about this has never gotten it to work in Ubuntu - bu

t I don't know what release they started at.  There's not much to that thread - but if you want to see it it is at: [http://ubuntuforums.org/showthread.php?t=2237021&page=2&p=13102731#post13102731](http://ubuntuforums.org/showthread.php?t=2237021&page=2&p=13102731#post13102731)

Thanks again for all the help here.  I wonder if there is a way to figure out which files from within the deb are actually the driver files and if they can just be moved to a folder somewhere.

---

### Post by dave131 on 2014-08-20
Is there anyway to find out what the actual contents of the file used to tell tar how/what to build for this actually says?  If I could get to that, perhaps there might be a way to pull out what needs to be done.

---

### Post by dave131 on 2014-08-21
Well, I had to reload Ubuntu 14.04 64-bit and now I'm back at the xterm error.  I can only believe it's a difference between 12.xx and 14.xx that allows you to do it but I have the problem.  So I tried doing the link again and now it won't let me.  Why?```
me@me-Studio-1735:~$ sudo link /lib/terminfo /usr/share/terminfo
link: cannot create link &#8216;/usr/share/terminfo&#8217; to &#8216;/lib/terminfo&#8217;: Operation not permitted
me@me-Studio-1735:~$ 
``` As far as I can remember this is exactly what I did with the previous install of 14.04 64-bit on this laptop.

---

### Post by steeldriver on 2014-08-21
... you should probably be creating a symlink

```

sudo **ln -s** /lib/terminfo /usr/share/terminfo

```

FWIW you can see what's in the deb.sh file using

```

strings lexmark-08z-series-driver-1.0-1.i386.deb.sh | less -N

```

- it's a ~300 line shell script followed by a big blob of binary data. I'm not sure how much you will be able to learn from that, but take a look.

---

### Post by dave131 on 2014-08-21
Thanks - adding the -s to make it symbolic did the trick.

When the installation says it failed, but before closing the gui, I'm able to copy the folder that the file extracted it's contents to and copy that folder so I can save it.  Having done so, I read in another thread (which of course I can't find again yet ;) ) where a lexmark engineer had given the instructions on how to capture that folder, then use tar to recreate the .deb - in that case to supposedly allow for 64-bit ubuntu.  The tar statement doesn't really list the files, etc., anywhere, but instead points to a file, instarchive_all, which apparently must contain the instructions or whatever to tar to build the .deb.  That's the file I can't seem to open in an editor either.  I'm assuming the header definitions, etc., are in that "control file", and since the installation process is complaining about the headers, I thought I'd try to see if I could change that somehow.

Mind you, I'm a newbie and don't know what the heck I'm doing! ;)  I'm just trying things that come to mind but perhaps none of it makes any sense and I shouldn't be doing it?

Thanks again for your help.

---

### Post by dave131 on 2014-08-21
I just found reference to at least part of that post I can't find:

sudo ./lexmark-08z-series-driver-1.0-1.i386.deb.sh --noexec --target lexmark

extracts the contents to the folder "lexmark" and doesn't try to execute the script.

 cd lexmark
tar xvf instarchive_all --lzma
 sudo dpkg -i --force-all lexmark-08z-series-driver-1.0-1.i386.deb


I did notice that instarchive_all is a huge file as well, so I'm not sure what it is.  

I'm probably WAY off base here since I don't know what I'm doing, so don't be afraid to say so - I'm just learning! ;)

BTW - here's the thread that gave me the idea that there is something inside o instarchive_all that is the actual driver and could somehow be loaded to ubuntu:

[http://forums.fedoraforum.org/archive/index.php/t-294123.html](http://forums.fedoraforum.org/archive/index.php/t-294123.html)

---

### Post by dave131 on 2014-08-21
I think I found a solution!!!  Kept searching the net and found this:

[http://askubuntu.com/questions/71424/how-do-i-get-a-lexmark-x4690-printer-working](http://askubuntu.com/questions/71424/how-do-i-get-a-lexmark-x4690-printer-working)

Since I didn't want to go through the stuff in step 3, I just followed the download link and got the file.  Then this appeared to work:```
me@me-Studio-1735:~/Downloads$ ls
lexmark-08z-series-driver-1.0-1.i386.deb.sh
lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz
New-lexmark-08z-series-driver-1.0-1.i386.deb.deb
selfgz5750
me@me-Studio-1735:~/Downloads$ sudo dpkg -i New-lexmark-08z-series-driver-1.0-1.i386.deb.deb
[sudo] password for me: 
Selecting previously unselected package lexmark-08z-series-driver.
(Reading database ... 211375 files and directories currently installed.)
Preparing to unpack New-lexmark-08z-series-driver-1.0-1.i386.deb.deb ...

--------------------------
Installing 08z-series-driver ...
--------------------------
Unpacking lexmark-08z-series-driver (1.0-1) ...
Setting up lexmark-08z-series-driver (1.0-1) ...
   -- Updating symbolic links
Apparmor cupsd exception done.



Installation Complete.
--------------------------------------------

Please remember to review the license agreement (license.txt)
at /usr/lexinkjet/08zero/docs/ before using this software.

me@me-Studio-1735:~/Downloads$
```

So, if it looks like it worked to you, I'll post some instructions back in the original thread to see if it helps the user there.  I've seen remarks on the web in my research that indicate this is a common driver to a lot of lexmark inkjets, and I believe a lot of Dell printers are also just rebranded Lexmarks, so it will be interesting to see.

Thanks for the help!

---

### Post by dave131 on 2014-08-22
Great news!!  The user in the other post said this worked great and they have it working both via USB and via wireless!!  They said they've been trying to get this to work for 2 years!

Perhaps a link to the above thread in askubuntu might be appropriate for Lexmark/Dell older inkjets?

---

