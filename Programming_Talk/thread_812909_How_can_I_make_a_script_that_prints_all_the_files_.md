---
title: "How can I make a script that prints all the files of a type in a directory?"
date: 2008-05-30
forum: Programming Talk
---

### Post by Belathor on 2008-05-30
Hi,

I really want to get back into using linux on a daily basis, but before I can I need to make backup files of a lot of my documents. Since these files are in an obscure proprietary windows format (.jnt), I know that I will not be able to access them in linux. Instead, I want to print them all to pdf and then backup those for use on linux. I installed a pdf printer so I know I can do that. I just have hundreds of files that would take hours and hours of mindless, repetitive clicking. I thought this might be the perfect task for writing a script.

Unfortunately, I'm not a CS or IT student, nor am I particularly knowledgeable about writing system scripts. I am not sure where to begin and I haven't found any support among my friends for helping me figure it out. 

I tried googling for "print all the contents of a folder" and "print all pdfs in a directory" but I really couldn't find anything useful.

So, I am wondering if anyone here could give me some pointers for solving this problem? Should I use python or could it be done easier with a batch file? Are there already scripts that will do this?

Thanks for your help!

---

### Post by Lau_of_DK on 2008-05-30
Hey,


I'm really not the go to guy on scripts, but how about 

"ls *.pdf | printer-software" and then just pipe the names?

Or maybe look in the thread that was here a few hours ago, about a "for loop" in bash.

Or thirdly, you could use a python script and the "os" lib ?

/Lau

---

### Post by Belathor on 2008-05-30
Thanks for the reply Lau!

Since this is on Windows (the only os that reads these stupid files), I don't have access to bash. So, it looks like I need to figure out how to do it with python and "os" lib. 

I don't suppose you know of any good resources with example scripts for doing file management operations in python by any chance?

---

### Post by LaRoza on 2008-05-30
> **Belathor said:**
> Thanks for the reply Lau!

Since this is on Windows (the only os that reads these stupid files), I don't have access to bash. So, it looks like I need to figure out how to do it with python and "os" lib. 

I don't suppose you know of any good resources with example scripts for doing file management operations in python by any chance?

You can list all files in a directory on Windows with the "dir" command.

```

dir *.pdf

```

I am not sure what you mean by "pdf-printer". Is this a physical printer or a converter? What application is it?

---

### Post by geirha on 2008-05-30
The script should be easy, even in batch, but you need a program that can convert or print .jnt-files from the cli. From what I can gather from google, only Microsoft Windows Journal Viewer can read .jnt-files, but I doubt it can convert or print them from the cli.

Try running the viewer from the cli with /? as argument.

---

### Post by Lau_of_DK on 2008-05-30
> **Belathor said:**
> Thanks for the reply Lau!

Since this is on Windows (the only os that reads these stupid files), I don't have access to bash. So, it looks like I need to figure out how to do it with python and "os" lib. 

I don't suppose you know of any good resources with example scripts for doing file management operations in python by any chance?

I'm sorry, then I missed the whole point :)

You still have the possibility of doing a little Python script like the one I mentioned. If you right-click one of these files, do you have the option to "print" ? If you do, find the print command in "regedit" under HKEY_CLASSES_ROOT and then the file-extension. Then simply make a script that walks over the output from a dir and runs that command with the filename as the parameter.

If you dont know how this is done exactly in Python, I'm sure there's about 300 hauling Pythoneers standing behind me, ready to write the script :)

/Lau

---

### Post by Belathor on 2008-05-30
> **geirha said:**
> The script should be easy, even in batch, but you need a program that can convert or print .jnt-files from the cli. From what I can gather from google, only Microsoft Windows Journal Viewer can read .jnt-files, but I doubt it can convert or print them from the cli.

Try running the viewer from the cli with /? as argument.

I ran "Journal /?" from the cli but it just opens the program. It doesn't give me any options.

I was hoping there was a way to print the file using whatever explorer uses to print from right click in explorer. That way I don't have to worry about find any conversion software because I'm pretty sure it doesn't exist.
------------
Edit:

> You still have the possibility of doing a little Python script like the one I mentioned. If you right-click one of these files, do you have the option to "print" ? If you do, find the print command in "regedit" under HKEY_CLASSES_ROOT and then the file-extension. Then simply make a script that walks over the output from a dir and runs that command with the filename as the parameter.

That is exactly what I am looking to do. I'm regedit right now and I have searched for the print command as well as the jnt extension. I found the .jnt extension but not the print command. The Find dialog brought up .printerExport though. Is that the print command? If so, I'm pretty baffled about how to use it.

---

### Post by Belathor on 2008-05-30
> **LaRoza said:**
> 
I am not sure what you mean by "pdf-printer". Is this a physical printer or a converter? What application is it?

Hi LaRoza,

I just downloaded a windows equivalent of "cups-pdf" and set that as my default printer. I'm trying to "print out" all of my Windows Journal files on my TabletPC in .pdf so that I can actually read them on linux.

---

### Post by Lau_of_DK on 2008-05-30
> **Belathor said:**
> 
That is exactly what I am looking to do. I'm regedit right now and I have searched for the print command as well as the jnt extension. I found the .jnt extension but not the print command. The Find dialog brought up .printerExport though. Is that the print command? If so, I'm pretty baffled about how to use it.

argh :( Normally there would be a little sub-tree to .jnt where you would have "shell" operations. But I'm suspecting that it might be printing via Rundll32.dll and executing those commands arent my strong-suit. 

I saw a similar thread on another forum, where the guy ends up using something called [http://www.cutepdf.com]("http://www.cutepdf.com") to get the job done. 

Dumb question: If you just copy all the files into 1 folder, select them all, right-click and choose print, what happends? :)


/Lau

---

### Post by durand on 2008-05-30
Yeah, I think you can just select all the files as Lau said and then right click, and print. You might have to change the default printer to the pdf one. There might also be a program that allows you to batch print in windows. There seem to be a lot of options here: [http://www.google.com/search?complete=1&hl=en&q=batch+print+windows&btnG=Google+Search](http://www.google.com/search?complete=1&hl=en&q=batch+print+windows&btnG=Google+Search)

---

### Post by Belathor on 2008-05-30
> Dumb question: If you just copy all the files into 1 folder, select them all, right-click and choose print, what happends? 

Lots of explosions (Journal crashed from opening up too many instances and I had to click ok a huge amount of times because of it) and then eventually a few of the documents asked me to print them. I think if I select 10 at a time, I can probably get everything transfered to pdf eventually. I think that may be faster than find a command to do what I want with a script.

Thanks for all your help!

---

### Post by Lau_of_DK on 2008-05-30
> **Belathor said:**
> Lots of explosions (Journal crashed from opening up too many instances and I had to click ok a huge amount of times because of it) and then eventually a few of the documents asked me to print them. I think if I select 10 at a time, I can probably get everything transfered to pdf eventually. I think that may be faster than find a command to do what I want with a script.

Thanks for all your help!

I was afraid that might happen. Let me know if CutePDF works out for you.

Also to the rest of you guys: Aren't there some Python-gurus who can sort this out? :)

/Lau

---

### Post by durand on 2008-05-30
My friend suggests using AutoIt or vbscript to interact with the gui. So it is graphical batch processing.

---

### Post by Mr.Macdonald on 2008-05-30
if you have a python interface just do this:

[PHP]
function fprint(indir, outdir):
	import os
	for i in os.listdir(indir):
		f = open(outdir+i, 'w')
		f.write = toPdf(indir+i).read()

fprint(Directory, Destination)
[/PHP]

replace the "f.write = toPdf(indir+i).read()" with the proper function to your program
and the Directory with a directory with files (not recursive) and Destination with the "Destination Directory"

---

