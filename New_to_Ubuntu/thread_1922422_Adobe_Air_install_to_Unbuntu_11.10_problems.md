---
title: "Adobe Air install to Unbuntu 11.10 problems"
date: 2012-02-08
forum: New to Ubuntu
---

### Post by tro1984 on 2012-02-08
Hi all, I've done some research here, and found [this]("http://ubuntuforums.org/showthread.php?p=11344792") on how to do it, however when I get to 

sudo ./AdobeAIRInstaller.bin 

this is what it says:

sudo: AdobeAIRInstaller.bin: command not found

Not sure what to do from here?

(I'm running 32 bit)

---

### Post by grahammechanical on 2012-02-08
You need to CD (change directory) into the directory/folder where you have put AdobeAIRinstaller.bin. Make sure that the command is correct and you are not using upper case characters where you should not use them. So,

AdobeAIRInstaller.bin & adobeairinstaller.bin are two different file names.

Regards.

---

### Post by tro1984 on 2012-02-09
> **grahammechanical said:**
> You need to CD (change directory) into the directory/folder where you have put AdobeAIRinstaller.bin. Make sure that the command is correct and you are not using upper case characters where you should not use them. So,

AdobeAIRInstaller.bin & adobeairinstaller.bin are two different file names.

Regards.

I've double and tripled checked those things, they are correct, the command prior:

  chmod +x AdobeAIRInstaller.bin 

worked fine.

---

### Post by Learning Linux 2011 on 2012-02-11
I'm not an expert, but isn't it supposed to be
```

chmod a+x AdobeAIRInstaller.bin

```

Also, are you sure you need the sudo part?

Also, I tried installing Adobe Acrobat Reader a few days ago and it was the buggiest program I have ever used in Linux.

---

### Post by tro1984 on 2012-02-11
> **Learning Linux 2011 said:**
> I'm not an expert, but isn't it supposed to be
```

chmod a+x AdobeAIRInstaller.bin

```

Also, are you sure you need the sudo part?

Also, I tried installing Adobe Acrobat Reader a few days ago and it was the buggiest program I have ever used in Linux.

I think I figured it out this morning.

I think the file was bad, I  deleted it, and redownloaded the file. After that, I had no problems doing it. Air is working fine now, and I didn't need the sudo part. Thanks for trying to help.

As for Acrobat reader, for now, the document viewer built into Ubuntu has been working fine for me. I've been skimming through sevreral Pathfinder PDFs the last few days while things download and update.

---

