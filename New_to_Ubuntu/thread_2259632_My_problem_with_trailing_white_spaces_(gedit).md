---
title: "My problem with trailing white spaces (gedit)"
date: 2015-01-05
forum: New to Ubuntu
---

### Post by sai7 on 2015-01-05
Hello, so I've installed Ubuntu for a while now. I'm still really new to Ubuntu, but I'm getting used to it. Since I always use gedit, I want to ask because I can't seem to find the answer.

So the question is "How do I remove trailing white space at the end of every document?"

I've seen a github repository of this, but I still can't seem to get it to work because it always tells me I don't have such files or directories called "trailsave.*" I do kind of see that it's searching for files with trailsave in its name, but it's still not working.

When I use Fire Fox and I look at the page source, for every page I make, I see the white space at the very end of the document. I transfer these files over to Windows and I open it up in NotePad++, I then see the actual trailing white space in the document itself. So this isn't the page source anymore, it's the actual document.

I want to remove these white spaces so that it doesn't waste bytes on my hard-drive or any storage I put them on.

I'm not sure if there's a program that can do this, but I'm willing to listen.

EDIT:

Here's the github repository I'm talking about.

[https://github.com/jonleighton/gedit-trailsave](https://github.com/jonleighton/gedit-trailsave)

---

### Post by whitesmith on 2015-01-05
This analysis may help you. If you open gedit and enter the following```
test
```and nothing more (don't press Enter!), and then save the file on your Desktop as test.txt, you can then open a terminal and do```
ls -l Desktop/test.txt
```and you'll see that it has 5 characters. The extra one is a newline that editors put there by convention. Your job is now to remove that final newline. A simple shell script could do the job. I'm about to get out of here or I would dash off something for you.

---

### Post by sandyd on 2015-01-05
> **sai7 said:**
> Hello, so I've installed Ubuntu for a while now. I'm still really new to Ubuntu, but I'm getting used to it. Since I always use gedit, I want to ask because I can't seem to find the answer.

So the question is "How do I remove trailing white space at the end of every document?"

I've seen a github repository of this, but I still can't seem to get it to work because it always tells me I don't have such files or directories called "trailsave.*" I do kind of see that it's searching for files with trailsave in its name, but it's still not working.

When I use Fire Fox and I look at the page source, for every page I make, I see the white space at the very end of the document. I transfer these files over to Windows and I open it up in NotePad++, I then see the actual trailing white space in the document itself. So this isn't the page source anymore, it's the actual document.

I want to remove these white spaces so that it doesn't waste bytes on my hard-drive or any storage I put them on.

I'm not sure if there's a program that can do this, but I'm willing to listen.

EDIT:

Here's the github repository I'm talking about.

[https://github.com/jonleighton/gedit-trailsave](https://github.com/jonleighton/gedit-trailsave)
```

head -c -1 /path/to/file
```
I suggest making sure the file does have a newline character.

---

### Post by sai7 on 2015-01-06
> **whitesmith said:**
> This analysis may help you. If you open gedit  and enter the following```
test
```and nothing more (don't press  Enter!), and then save the file on your Desktop as test.txt, you can  then open a terminal and do```
ls -l Desktop/test.txt
```and you'll  see that it has 5 characters. The extra one is a newline that editors  put there by convention. Your job is now to remove that final newline. A  simple shell script could do the job. I'm about to get out of here or I  would dash off something for you.

Thanks, yes. That is what I'm talking about. I'm not sure if I said the term correctly, but that's what I'm trying to do. I want to remove the extra line break at the end of the document because this only happens with gedit (in my experince).

> **sandyd said:**
> ```

head -c -1 /path/to/file
```
I suggest making sure the file does have a newline character.

Well, no. All of my documents don't have any starting or ending line breaks. It always adds it in Ubuntu for some reason. When I'm on gedit, I don't see any trailing line breaks. Wehn I save it and view the page sources, that's when I start to see an extra line break at the end.

As I mentioned earlier, I transfer these files to Windows and view them in NotePad++, I also see the trailing line break at the very end of the documents. I've tried this multple ways. I've saved files onto my Windows which I know for sure doesn't have trailing line breaks at the end. Then I transfer them over to Ubuntu and once I save it with gedit, the line breaks show up again.

Note: I meant to say trailing line breaks. Not trailing white space. I'm not sure if they're different, but my problem is actually dealing with extra line breaks at the end of every document.

---

### Post by bab1 on 2015-01-06
> **sai7 said:**
> Thanks, yes. That is what I'm talking about. I'm not sure if I said the term correctly, but that's what I'm trying to do. I want to remove the extra line break at the end of the document because this only happens with gedit (in my experince).



Well, no. All of my documents don't have any starting or ending line breaks. It always adds it in Ubuntu for some reason. When I'm on gedit, I don't see any trailing line breaks. Wehn I save it and view the page sources, that's when I start to see an extra line break at the end.

As I mentioned earlier, I transfer these files to Windows and view them in NotePad++, I also see the trailing line break at the very end of the documents. I've tried this multple ways. I've saved files onto my Windows which I know for sure doesn't have trailing line breaks at the end. Then I transfer them over to Ubuntu and once I save it with gedit, the line breaks show up again.

Note: I meant to say trailing line breaks. Not trailing white space. I'm not sure if they're different, but my problem is actually dealing with extra line breaks at the end of every document.

I believe it's because Linux uses a slightly different method to end lines than Windows does.  The difference is CR vs CR/LF.  The white space is a Carrage Return without a Line Feed. See if [this info]("http://askubuntu.com/questions/426660/change-newline-character-in-gedit") helps you.  You can save files as "Windows" type.  Try saving a file (*save as*) and changing the type look for the button at the bottom

---

### Post by sai7 on 2015-01-06
> **bab1 said:**
> I believe it's because Linux uses a slightly different method to end lines than Windows does.  The difference is CR vs CR/LF.  The white space is a Carrage Return without a Line Feed. See if [this info]("http://askubuntu.com/questions/426660/change-newline-character-in-gedit") helps you.  You can save files as "Windows" type.  Try saving a file (*save as*) and changing the type look for the button at the bottom

Well, I just confirmed that it's just gedit that's doing that. I installed Blue Fish and tested it out and it doesn't have any trailing line breaks. Once I make an edit and save it in gedit, it adds the trailing line break. I've saved it as Windows and I still get the same thing.

I love gedit and I think it's simple and easy to use. I don't want to switch to Blue Fish if there's a command or few files or something that can remove the extra line break in gedit.

---

### Post by Impavidus on 2015-01-06
In Windows the convention is to use a carriage return followed by a line feed character as a line *separator*. This convention comes from the teletype days. In Linux the convention is to use a line feed character as a line *terminator*. Being a terminator instead of a separator, an extra line feed is appended to the last line. Some tools rely on this line terminator and may get confused when they see a file end in the middle of a line. This final line terminator makes a one line text file in Linux a single byte longer than in Windows. On the other hand, you save one byte at all other line ends. But what is a single byte these days, when you can fit a trillion bytes on a hard drive?

I don't have gedit here. I think in most text editors you can choose to omit the final line terminator or use the Windows convention of using CR/LF to separate lines. Most text editors on Windows and Linux will recognise eachs others convention, as well as the Mac convention (which terminates lines using a singe carriage return).

---

### Post by coldraven on 2015-01-06
What you need to do:
Install git
```
sudo apt-get install git
```
Then get the git repositry
```
git clone https://github.com/jonleighton/gedit-trailsave
```
Then open the trailsave folder 
```
cd gedit-trailsave/
```
Then run the install script
```
./install.sh
```
You should now see "Trailsave installed! Now restart Gedit and active the plugin in Edit > Preferences."
Do that and you should be in business

---

### Post by whitesmith on 2015-01-06
The answer I gave was based on your stated intention to bring up the files in notepad++, a Windows program. If you plan to use these files in Ubuntu, leave the terminating newline there as sandyd et al have recommended. Also, why are you so concerned with removing a single byte from a file? Even if you had 500K text files on your computer eliminating the terminating newline would only save 500 KB, an insignificant amount by today's HD standards. Also, as has been pointed out, the mark tells Linux something. Eliminate it and you may have serious problems if you try to read the file in other than Windows. I hope this sums it up: Many minuses, few pluses.

---

### Post by sai7 on 2015-01-06
> **coldraven said:**
> What you need to do:
Install git
```
sudo apt-get install git
```
Then get the git repositry
```
git clone https://github.com/jonleighton/gedit-trailsave
```
Then open the trailsave folder 
```
cd gedit-trailsave/
```
Then run the install script
```
./install.sh
```
You should now see "Trailsave installed! Now restart Gedit and active the plugin in Edit > Preferences."
Do that and you should be in business

Tried it and I still get the same results. Nothing changed.

> **whitesmith said:**
> The answer I gave was based on your stated  intention to bring up the files in notepad++, a Windows program. If you  plan to use these files in Ubuntu, leave the terminating newline there  as sandyd et al have recommended. Also, why are you so concerned with  removing a single byte from a file? Even if you had 500K text files on  your computer eliminating the terminating newline would only save 500  KB, an insignificant amount by today's HD standards. Also, as has been  pointed out, the mark tells Linux something. Eliminate it and you may  have serious problems if you try to read the file in other than Windows.  I hope this sums it up: Many minuses, few pluses.

The whole point isn't to just be read on 1 OS, the actual point is so that I can upload it to my web server. If I happen to have empty line breaks or trailing white spaces before the HTML document starts, I'll most likely end up with a blank white page. Therefore, my concern affects the main point greatly if I don't remove extra line breaks or trailing white spaces. Since I'm using PHP, if there is a trailing white space in between 3 files and it appears in the second file, it'll most likely give me a blank page because the white space is interfering with the HTML headers.

I don't want to be editing in Notepad++ because I have 2 different localhost I'm working on and I can't keep logging off and logging back on just to transfer the files.

It's ok if this can't be helped. Seems like the longer I post, the longer this just keeps circling in loops. I guess I'll shut up now.

---

### Post by JeQhdMD on 2015-01-06
Eom . . do the character encoding/line ending options in gedit (save as linux/unix, mac, windows) make any difference?

---

### Post by coldraven on 2015-01-06
> because it always tells me I don't have such files or directories called "trailsave.*"
You are searching for the wrong name, the directory is call gedit-trailsave

> Tried it and I still get the same results. Nothing changed.
Do you mean you managed to install it and it did not remove the white space?
I followed  the steps in my previous post and it installed easily.

---

