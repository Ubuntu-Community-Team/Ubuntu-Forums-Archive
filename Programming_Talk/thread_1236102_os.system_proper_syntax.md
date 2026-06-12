---
title: "os.system proper syntax"
date: 2009-08-09
forum: Programming Talk
---

### Post by dalandtwist on 2009-08-09
Hello,

I have python script that looks at a file structure and parses it out.  That all works fine.
then I am running ffmpeg using what I have previously defined to create some mpegs.
I am getting errors in syntax in the os.system line.  Can anyone see where I am going wrong?  Basicallly I am trying to replace the variable fileRawName in my ffmpeg command.

thanks,
david
-------------------

def LaunchNuke(self):
    mypath = self.lblImgSeqname.get()
    (dirName,fileName) = os.path.split (mypath)
    (fileBaseName, fileExtension) = os.path.splitext(fileName)
    (fileRawName, fileFrameNumber) = os.path.splitext(fileBaseName)

    os.system ("ffmpeg -i 'fileRawName'%04d.jpg -vcodec libx264 -threads 0 'fileRawName'.mpeg") 
--------------------

---

### Post by unutbu on 2009-08-09
[PHP]os.system ("ffmpeg -i %s%04d.jpg -vcodec libx264 -threads 0 %s.mpeg"%(fileRawName,fileFrameNumber,fileRawName)) [/PHP]

---

### Post by spupy on 2009-08-10
I would recommend the "command" module (or was it commands). With it you can capture the output of the program and its exit status.

---

