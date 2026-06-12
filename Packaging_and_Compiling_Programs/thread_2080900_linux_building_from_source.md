---
title: "linux building from source"
date: 2012-11-05
forum: Packaging and Compiling Programs
---

### Post by Kevin McCready on 2012-11-05
A less than helpful person advised me there were 109 000 000 google hits for "linux building from source". In fact there are 2,240. Half an hour of searching brought me no closer to enlightenment.

I have to figure out how to solve this error message:
Please make sure the TESSDATA_PREFIX environment variable is set to the parent directory of your "tessdata" directory.

I have found the directory and its parent (tesseract-ocr) but I don't know how to do anything else. 

All more than less than helpful help would be appreciated.

---

### Post by nothingspecial on 2012-11-05
well you set an environment variable using the export command
```

export TESSDATA_PREFIX=/path/to/the/parent/directory
```

You might get better help if you explained what your are trying to build from source and to what purpose.

---

### Post by Kevin McCready on 2012-11-05
Thanks, I'm trying to install tesseract. I did this which seemed to work:

export TESSDATA_PREFIX=/usr/share/tesseract-ocr/

then I get this error:

k@k-Presario-CQ57-Notebook-PC:~$ export TESSDATA_PREFIX=/usr/share/tesseract-ocr/
k@k-Presario-CQ57-Notebook-PC:~$ tesseract /home/k/Downloads/t.tif output
Error opening data file /usr/share/tesseract-ocr/tessdata/eng.traineddata
Please make sure the TESSDATA_PREFIX environment variable is set to the parent directory of your "tessdata" directory.
Failed loading language 'eng'
Tesseract couldn't load any languages!
Could not initialize tesseract.

---

### Post by Impavidus on 2012-11-05
Your problem does not sound as one that requires building linux from source. As mentioned, use
```
export TESSDATA_PREFIX=/path/to/tesseract-ocr
```You may want to put that line of code in some file that is automatically processed, like .bashrc in your home directory or (if you start the program from a graphical menu) in .xsessionrc (also in your home directory), as suggested here: [http://askubuntu.com/questions/82120/how-do-i-set-an-environment-variable-in-a-unity-session](http://askubuntu.com/questions/82120/how-do-i-set-an-environment-variable-in-a-unity-session). That way you won't have to enter the export command every day again.

EDIT: Your program definitely tries to locate a file in the directory you specified, so setting the environment variable is not your problem.

---

### Post by nothingspecial on 2012-11-05
Why do you not just use the package from the repositories ?

---

### Post by Kevin McCready on 2012-11-05
Actually I did try the repos for Lubuntu 11.10 but they didn't have tesseract 3. 

So I tried ppa, no luck. Now I when I try to update I get an error:

W: Failed to fetch [http://ppa.launchpad.net/alex-p/notesalexp/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/alex-p/notesalexp/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/alex-p/notesalexp/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/alex-p/notesalexp/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

So then I added this to my sources.list

*deb 	[http://notesalexp.net/debian/oneiric/](http://notesalexp.net/debian/oneiric/) oneiric main*

gImageReader is also supposed to be a gui for tesseract but I can't get that working either.

The reason for my first post, is that I was trying to solve the problem step by step with each error message.

I'd sorta like to begin by removing the update error, then trying to get tesseract 3 working then gImageReader

---

### Post by snowpine on 2012-11-05
Tesseract 3 is in 12.04 repos. 12.04 is a long-term-support release through April 2017, whereas support for your 11.10 ends in April. An obvious choice in my opinion.

If you must compile Tesseract then they have very clear instructions on their homepage, which I'm assuming you haven't seen since you haven't made any reference to them: [http://code.google.com/p/tesseract-ocr/wiki/Compiling](http://code.google.com/p/tesseract-ocr/wiki/Compiling)

Typically when users on these forums get stuck with instructions like that, they achieve success by carefully going step-by-step and posting the complete output of each command in the forums.

---

### Post by oldos2er on 2012-11-05
Moved to Packaging and Compiling Programs.

---

