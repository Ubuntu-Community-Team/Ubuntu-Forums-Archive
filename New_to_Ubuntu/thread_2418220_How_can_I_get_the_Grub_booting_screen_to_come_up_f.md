---
title: "How can I get the Grub booting screen to come up first?"
date: 2019-05-03
forum: New to Ubuntu
---

### Post by billy3xs on 2019-05-03
My Windows 8 starts with an MSI boot window that I can hit F11 to get into and select Ubuntu, then the Ubuntu Grub booting screen to choose Ubuntu or Win. 
Otherwise it boots Win8 and skips the Grub boot window.

**How can I get the Grub booting screen to come up first? **
So, then I can use Grub Customizer to remember which OS was running last as a default boot (for the wife).:p
[ATTACH=CONFIG]283163[/ATTACH][ATTACH=CONFIG]283162[/ATTACH]

---

### Post by jeremy31 on 2019-05-03
It is likely in BIOS somewhere, custom EFI setting to boot a different efi file or maybe even a OS boot manager.  You might be able to change in Ubuntu, post results from terminal for
```
efibootmgr
```

---

### Post by oldfred on 2019-05-03
Post this:
sudo efibootmgr -v

Most system this will work, but a few reset and only changes from within UEFI stick and then only with newer UEFI from vendor.
Check current order & hex number of each entry:
sudo efibootmgr -v
Change boot order with efibootmgr, some require all 4 hex char others 1 char is ok.
sudo efibootmgr -o 0,1,2
see also 
man efibootmgr
[http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr](http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr)

---

### Post by billy3xs on 2019-05-03
billy2xs@billy2xs-MS-7885:~$ efibootmgr
BootCurrent: 0001
Timeout: 1 seconds
BootOrder: 0000,0001,0005,0003,0004,0002
Boot0000* Windows Boot Manager
Boot0001* ubuntu
Boot0002* UEFI: Built-in EFI Shell 
Boot0003* Hard Drive 
Boot0004* CD/DVD Drive 
Boot0005* ubuntu

also the screen;

[ATTACH=CONFIG]283164[/ATTACH]

---

### Post by billy3xs on 2019-05-03
Cowabunga!
billy2xs@billy2xs-MS-7885:~$ sudo efibootmgr -v
[sudo] password for billy2xs: 
BootCurrent: 0001
Timeout: 1 seconds
BootOrder: 0000,0001,0005,0003,0004,0002
Boot0000* Windows Boot Manager    HD(2,GPT,59e6db12-beb5-48e4-94ee-ea48d8595718,0x96800,0x31800)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...8................
Boot0001* ubuntu    HD(2,GPT,59e6db12-beb5-48e4-94ee-ea48d8595718,0x96800,0x31800)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0002* UEFI: Built-in EFI Shell     VenMedia(5023b95c-db26-429b-a648-bd47664c8012)..BO
Boot0003* Hard Drive     BBS(HD,,0x0)..GO..NO........o.C.r.u.c.i.a.l._.C.T.5.0.0.M.X.2.0.0.S.S.D.1....................A...........................>..Gd-.;.A..MQ..L. . . . . . . . .5.1.6.4.1.1.3.1.A.0.3.8........BO
Boot0004* CD/DVD Drive     BBS(CDROM,,0x0)..GO..NO........o.A.S.U.S. . . . .D.R.W.-.2.4.B.1.S.T. . . .j....................A...........................>..Gd-.;.A..MQ..L.5.F.0.D.L.C.5.0.1.5.5.4. . . . . . . . ........BO
Boot0005* ubuntu    HD(2,GPT,59e6db12-beb5-48e4-94ee-ea48d8595718,0x96800,0x31800)/File(\EFI\UBUNTU\GRUBX64.EFI)..BO

---

