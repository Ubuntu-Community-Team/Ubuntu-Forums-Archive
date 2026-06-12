---
title: "Samba VFS recycle bin"
date: 2016-05-23
forum: New to Ubuntu
---

### Post by gemmajid on 2016-05-23
Hello,

i'm using ubuntu 16.04 with samba enabled on it. I have configured samba recycle bin [FONT=Ubuntu, Arial, libra sans, sans-serif][COLOR=#111111]& set my existing partition as samba recycle repository but whenever i delete file it's just create file path and file goes missing.[/COLOR][/FONT]

[FONT=Ubuntu, Arial, libra sans, sans-serif][COLOR=#111111]For Instance,[/COLOR][/FONT]

[FONT=Ubuntu, Arial, libra sans, sans-serif][COLOR=#111111]If i delete[/COLOR][/FONT]

[FONT=Ubuntu, Arial, libra sans, sans-serif][COLOR=#111111]/TestShare/TestFolder/TestFile.doc[/COLOR][/FONT]

[FONT=Ubuntu, Arial, libra sans, sans-serif][COLOR=#111111]in Deleted Repository only folders are available [/COLOR][/FONT]

[FONT=Ubuntu, Arial, libra sans, sans-serif][COLOR=#111111]/[/COLOR][/FONT][COLOR=#111111][FONT=Ubuntu]TestShare/TestFolder/

[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]if i set [/FONT][/COLOR].recycle[COLOR=#111111][FONT=Ubuntu] folder in my shared samba directory then samba recycle working fine[/FONT][/COLOR]

[TABLE]
[TR]
[TD="class: votecell"][CENTER][favorite]("http://askubuntu.com/questions/186057/samba-recycle-bin-in-ubuntu-12-04#")[COLOR=#6A737C][/COLOR]
[/CENTER]
[/TD]
[TD="class: postcell"]I have upgraded my ubuntu 10.04 server to Ubuntu 12.04, after setting samba i'm facing few problems, samba recycle bin not working properly, i have set my existing partition as samba recycle repository but whenever i delete some thing samba just make folder tree but the deleted file is missing.
for example,
I delete :
/Audit-Data/SambaTest/test.doc
so in delete-files it shows :
/Audit-Data/SambaTest/
The file is missing.
if i set .recycle folder in my shared samba directory then samba recycle working fine.


[/TD]
[/TR]
[/TABLE]

---

