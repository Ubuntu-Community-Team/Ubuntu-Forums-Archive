---
title: "Use grub2 to test filesystem issue"
date: 2008-08-02
forum: Outdated Tutorials &amp; Tips
---

### Post by bean123 on 2008-08-02
When you encounter booting issue with grub4dos, most often in the form of "Error 15: file not found" or "Error 16: Inconsistent file system structure", you can also try grub2.

First, you need to download my latest bootable cdrom image of grub2 at:

[http://grub4dos.sourceforge.net/grub2/](http://grub4dos.sourceforge.net/grub2/)

To start grub2 from XP/Vista boot manager, extract g2ldr.mbr, g2ldr and /boot/grub directory to one of your partition, for example, C:\, then add the following item in boot.ini:

C:\g2ldr.mbr="Start GRUB2"

If you're using vista, you can use g2ldr as boot file. This method is more reliable, as it skips the problematic g2ldr.mbr, thus avoiding the "NTFS5: No g2ldr" issue. If you are using XP and do encounter that issue, you need to defrag your system drive.

After grub2 starts, you can see the grub2 boot menu. Press 'c' to enter console mode. Here are some useful commands:

**ls**
Use `ls' to list file or devices. Use `ls' alone to find out the available devices. `ls -l' to show more information about them, like file system, label and uuid. Then, use ls to list files in your wubi directory, like:

ls (hd0,0)/ubuntu/install/boot/

**crc**
crc can be used to get the crc32 checksum of files. This is useful when you try to find out if the file is read correctly, for example:

crc (hd0,0)/ubuntu/install/boot/vmlinuz

Write down the number. Then inside windows, use some tool to get the crc checksum of vmlinuz and compare the results.

**search**
This is the equivalence of find --set-root in grub4dos. For example, the following command will search all partitions for file /ntldr and set the root device once it's found:

search -s -f /ntldr

search can also search partition using label or uuid.

**linux and initrd**
These two command can be used to boot the linux kernel.

If the problem is still present in grub2, there is a good chance that it's indeed a file system related issue. In this case, you can download fstest.exe from:

[http://grub4dos.sourceforge.net/grub4dos/](http://grub4dos.sourceforge.net/grub4dos/)

and run some tests inside windows:

fstest info C:\
fstest inode C:\$MFT
fstest inode C:\.
fstest list C:\
fstest list C:\ubuntu\install\boot
fstest inode C:\ubuntu\install\boot\vmlinuz
fstest comp C:\ubuntu\install\boot\vmlinuz

---

### Post by liyanricaoqiyue1314 on 2008-09-15
[size=2]Nude-calendar 1177, human and Shouzu the third "Battle of Lawson," Lawson barriers on the ground before the start of the Gap. [Runescape Gold](http://www.runescape-shop.com/runescape-gold/runescape-gold.php)This is a historic campaign, the campaign is "human beast seven years of war" in the first three major campaigns, the history of bare-called "people's car used to launch the war." [Runescape Power leveling](http://www.runescape-shop.com/runescape-power-leveling/runescape-power-leveling.php)Because, the bare-three million migrant workers has made in a month-20,000 warships, and timely expansion to the navy,[Runescape Powerleveling](http://www.runescape-shop.com/runescape-power-leveling/runescape-power-leveling.php) so that mankind has made the absolute superiority in the sea, with both sides of the back to. And the barren Shouzufengru the mainland until the 37th of the people of God the outbreak of war. [runescape shop](http://www.runescape-shop.com/)And it is precisely because of this campaign, the first time in the bare-war history, referred to the "Portland Ruo-yun," the name, many historians experts to the expansion of the war of special significance. Some people even said that, if not the war, as there will be a great hero was inspired by, of course, will be impossible for a human return to the mainland seven glorious history. [age of conan power leveling](http://www.aoc-power-leveling.org)Moreover, we said to this great man, in this war also made a bit of good results? [Runescape Gold Farm](http://www.runescape-shop.com/runescape-gold-farm/runescape-gold-farm.php)Portland Ruo-yun from Lawson on the Fort Fangyanwangqu, with both sides of the narrow ground to beat the Shouzu row over the army. [aoc power leveling](http://www.aoc-power-leveling.org)A tall face of ferocious ethnic people Zhengning the claws, but the body is more moderate and flexible people who foot, body, wrapped in a layer of black scales in the long tentacles of the Long Tuzhuo ethnic people. Of course, the master control of the air wing wizard and although their number less, but also with the team in the final, when prone radio ready siege of human soldiers guarding the wall. [/size][size=2][buy age of conan power leveling](http://www.aoc-power-leveling.org)Mankind's troops began to open Lawson barriers, 200,000 of the green collar Tieqi, hidden in two wings of the Tieqi second only to God bow of the 50,000 camp bow riders, and are in the final of the 300,000 Yazhen infantry. [buy aoc power leveling](http://www.aoc-power-leveling.org)Interval between the two sides about two kilometers distance from each other to see the other side of the bright banner of omnipresent there shaking. Ma Si Ming and the anger of the arms occasionally break out the [Runescape money](http://www.runescape-shop.com/runescape-gold/runescape-gold.php)sound of the collision, but the two sides is almost non-soldiers heard voices, the silence before the war that is reinforced by the kind of Qishixiongxiong Fengyuyulai. [Runescape Mini Game](http://www.runescape-shop.com/rs-mini-game/runescape-mini-game.php)The weather has also Laicourenao this time, to beat the dark clouds gradually from the [Rs Power leveling](http://www.runescape-shop.com/runescape-power-leveling/runescape-power-leveling.php) floating over the horizon, live coverage of the original is also clear skies, Yuan Yidian gradually so that the soldiers almost clear of each other's faces, the temperature suddenly dropped. So many people and irritable, even more tense over the past fainted. [Rs Gold](http://www.runescape-shop.com/runescape-gold/runescape-gold.php)Line-up finish. Last night talk election effort a silvery white armor, general Pigua&#24471;&#19981;skin to stay one point, struggling carrying a spear, at the moment Lawson body trembling from the Fort-Ruo-yun, although aware that this time only The first student, is not played with, but on the battlefield or Sheyu powerful Shaqi, the lack of tension in the Tuiruan body. [/size]

---

### Post by UsTBo8xo on 2008-10-18
**[[color=red]Buy Ads[/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Test drive our brand new real-time traffic estimator and create your campaign. Choose text, banner, or interstitial ads. Target by site, keyword, demographic. Create or upload multiple ads. **[[color=red]Sell Ads[/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)**Find out how we can help you generate more revenue from your ad space. Customize ads to match your site Approve and reject ads for your site Works alongside other ad programs [**[size=3][color=red]Make money online,now![/color][/size]**[color=#0000cc][/color]](http://www.adbrite.com/mb/landing_both.php?spid=95218)

---

### Post by dakkar9999 on 2008-11-15
Link not working at the moment.

---

### Post by tqzxzjhu on 2008-11-18
[&#27743;&#24178;&#21306;&#31649;&#36947;&#30095;&#36890;](http://classad.dahangzhou.com/223685.html)[&#35199;&#28246;&#21306;&#31649;&#36947;&#30095;&#36890;](http://classad.dahangzhou.com/223685.html)[&#25329;&#22661;&#21306;&#31649;&#36947;&#30095;&#36890;](http://classad.dahangzhou.com/223685.html)[&#19978;&#22478;&#21306;&#31649;&#36947;&#30095;&#36890;&#20844;&#21496;](http://classad.dahangzhou.com/223685.html)[&#19979;&#22478;&#21306;&#31649;&#36947;&#30095;&#36890;&#20844;&#21496;](http://classad.dahangzhou.com/223685.html)

---

### Post by chimera200 on 2008-12-01
Is there a working link for this still?

---

### Post by ago on 2008-12-02
[http://download.gna.org/grub4dos/](http://download.gna.org/grub4dos/)

---

### Post by patman0623 on 2008-12-23
Does this have anything to do with the poor handling of hard reboots? There's little more obnoxious than having to wait 90 minutes while chkdsk scans every cluster of my hard drive.

---

### Post by LRTIMKEN on 2008-12-30
You wrote's nice and I support you![NSK](http://www.nskcn.com/product/ShowClass.asp?ClassID=28) [nsk](http://www.nskcn.com/product/ShowClass.asp?ClassID=28) [NSK](http://www.9skf.cn/product/ShowClass.asp?ClassID=28) [nsk](http://www.9skf.cn/product/ShowClass.asp?ClassID=28)

---

### Post by bean123 on 2008-12-31
It seems sf.net doesn't allow directory listing any more, but you can still download the file with direct link:

fstest:
[http://grub4dos.sourceforge.net/grub4dos/fstest.exe](http://grub4dos.sourceforge.net/grub4dos/fstest.exe)

As for grub2 cd image, use this link (maybe a little slow):
[http://nufans.net/grub4dos/grub2/](http://nufans.net/grub4dos/grub2/)

BTW, I've assembled a msys/mingw tool kit that would allow to compile grub4dos/grubutil/grub2 inside Windows, you can download it at:
[http://download.gna.org/grub4dos/grub_msys_v4.zip](http://download.gna.org/grub4dos/grub_msys_v4.zip)

There are scripts to make it easier:

grub4dos_update, grubutil_update, grub2_update
Download the latest source code from svn.

grub4dos_build, grubutil_build, grub2_build
Build binary package.

---

### Post by 60hbe16es52 on 2009-01-12
is [jordan shoes](http://www.smkings.com) good enough for play basketball?

---

