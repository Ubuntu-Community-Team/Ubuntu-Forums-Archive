---
title: "Renaming a Directory or Copying and moving its files"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by iKant on 2008-05-18
Forewarning: I am a noob to ubuntu/terminal etc.

After installing ubuntu(hardy heron) I had to get a wireless driver and in the process extracted the .tar.gz into my "Documents" directory. [LIST=1]
[*]Is it possible for me to move these files without screwing up the already loaded and running drivers?
[*]If so what command(s) do I run to either rename the directory or copy and move all of the files in the directory? 
[/LIST] 
I've seen the commands 'mkdir','cp','mv' etc. but am confused on how I would get the contents of "Documents" into the new one without doing "mv" for every single file.

Also if you know any awesome terminal guides please link me, everyone I have found lacks depth in their explanations and reading 'man' on most commands just leaves me more confused.

Thanks for any help in advance!

---

### Post by Nepherte on 2008-05-18
You can also move a directory and all its content with the 'mv' command:
```
mv currentdirectory newdirectory
```
or are all the files of the tar.gz archive in Documents and not in a submap?

---

### Post by kellemes on 2008-05-18
Will this help?
[https://help.ubuntu.com/community/UsingTheTerminal]("https://help.ubuntu.com/community/UsingTheTerminal")

---

### Post by iKant on 2008-05-18
@Nepherte: I'm not sure exactly what you are asking but everything that was in the .tar.gz is in my docs now:
```
laptop:~$ ls Documents
AMD64         bcmwlnpf.sys  data2.cab       MFC71.DLL    setup.iss
ATL71.DLL     bcmwlpkt.dll  DellInfo64.exe  msvcp71.DLL  Version.txt
bcm1xsup.dll  bcmwls32.exe  DellInfo.exe    msvcr71.DLL  WLBCGCBPRO731.DLL
BCMLogon.dll  bcmwls64.exe  dellinst.exe    preflib.dll  wltray.exe
Bcmnpf64.sys  bcmwls.ini    DRIVER          r151517.exe  wltrynt.dll
bcmwlcpl.cpl  bcmwltry.exe  ikernel.ex_     README.rtf   wltrysvc.exe
bcmwlhlp.cab  bcmwlu00.exe  is.exe          setup.exe
bcmwlhlp.chm  data1.cab     launcher.ini    Setup.ini
bcmwliss.dll  data1.hdr     layout.bin      setup.inx
laptop:~$ 

```
Would I be okay just renaming the dir and creating a new documents directory? Or since I've already installed the setup.exe aren't all these files redundant, can't I delete them?

@kellemes: Yea thanks, I've been reading some third-party tuts directed towards windows converts :/

---

### Post by hyper_ch on 2008-05-18
```

mv /path/to/current/dir /path/to/new/dir
```

---

### Post by iKant on 2008-05-18
Thanks all of you, I ended up using a little of everything each of you said.

---

