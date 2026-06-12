---
title: "Finding and deleting directories and files with similar names"
date: 2013-03-16
forum: New to Ubuntu
---

### Post by gefalu2008 on 2013-03-16
On my computer there are about 900 redundant internet folders with the extension 
"_files". In addition there are the corresponding .htm or .html files. These files
are not within the folders having the extension "_files". They are within the 
same directories as the folders having the extension "_files"

The redundant folders are all over the place, in various directories. And now is the
time to get rid of them. And the associated htm and html files.

What would be the best way to carry out the purge with a few command-line 
operations?

I only know how to find the folders: 

**$ find ~ -name \*\\_files\* > folders.txt**

produces a text list of the redundant folders I have.

But then what I would like to do is to 

- take the name of each folder without its _files extension
- delete the corresponding .htm or .html file
- delete the folder
- and move on recursively to other directories

So how can I capture the name of each folder and use it to 
delete first the similarly named htm/html file and then 
to delete the folder itself?

Please can you help me? 900+ thanks if you can.

---

### Post by sudodus on 2013-03-16
Will this command list 'remove commands for all the files you want to remove, but no other files'? Try it (it only lists the commands due to ***echo***.)
```
sudo find ~ -name "*_files*" -exec echo rm -r {} \;
```
If you are happy with it, remove 'echo' from the line and run the real command.

Warning: it will remove all files in the directories matching the search pattern. Is this what you want?

---

### Post by vasa1 on 2013-03-16
Just to be clear, you want to get rid of both the htm/html file **and** its associated folder?

---

### Post by gefalu2008 on 2013-03-16
Yes that is right, I want to get rid of both the htm/html file and its associated folder.

---

### Post by sudodus on 2013-03-16
Then I think you dare try the command I suggested in post #2 :-)

---

### Post by gefalu2008 on 2013-03-16
Thank you - I am new to this so I do not understand what makes this command to delete the htm or html files as well. I must be reading your suggestion somehow incorrectly. To me it seems it deletes only the folders.

The htm or html files are not inside the folders having the extension "_files". The htm or html files are in the same directories as the  folders having the extension "_files".

I edited my original posting to make it more clear - sorry about having to speak about "files in folders having the extension '_files'".

---

### Post by steeldriver on 2013-03-16
OK so how about something like

```

while read -r -d $'\0' dir; do echo rm "${dir%_files}".html && echo rmdir "$dir"; done < <(find . -type d -name '*_files' -print0)

```

or if you want to use your folders.txt file,

```

while read -r dir; do echo rm "${dir%_files}".html && echo rmdir "$dir"; done < folders.txt

```

---

### Post by sudodus on 2013-03-16
> **gefalu2008 said:**
> Thank you - I am new to this so I do not understand what makes this command to delete the htm or html files as well. I must be reading your suggestion somehow incorrectly. To me it seems it deletes only the folders.

The htm or html files are not inside the folders having the extension "_files". The htm or html files are in the same directories as the  folders having the extension "_files".
I see. Have you still got the file with all the files to be deleted, that you wrote about in the opening post (OP)? Then you have the paths to the directories containing the "_files" directories.

Are these the ***only*** htm and html files in each of those particular directories? Or are there other files with the same extensions there? There is a risk that you delete files, that you want to keep, so you ***probably need to separate them manually, if there are files you want to keep in those directories***.

But if you want to delete them all, you can try the following command
```
 for i in $(sudo find ~ -name "*_files*"|sed s/_files.*/*.htm*/); do echo rm "$i"; done
```
Check that it 'wants' to remove the htm and html files you want to get rid of but no other files. If it is OK, you can remove ***echo*** from the command and run the real thing.

---

### Post by gefalu2008 on 2013-03-16
Thanks for the words of wardning. I have taken precautions - there is an up to date safety copy of my home folder. 

I think we are close now. The htm/html names contain empty spaces. The code seems to be trying to delete each word of the file names separately. I shall also test the interesting suggestion by Steeldriver.

---

### Post by steeldriver on 2013-03-16
... you may need to change the .html to .htm* in my version - if you have both suffixes

---

### Post by gefalu2008 on 2013-03-16
I tried

**while read -r dir; do echo rm "${dir%_files}".html && echo rmdir "$dir"; done < folders.txt**

Very nice! I am impressed! The code removes htm/html files alright - if there is only one such file in a directory. If there are 2, one is left. Also the folders with extension "_files" remain. But this cannot be far from the goal.

---

### Post by steeldriver on 2013-03-16
The folders won't be deleted unless they are empty - that's kind of a safety feature of rmdir - if you're SURE you want to delete non-empty directories, replace 'rmdir' by 'rm -rf'

If htm / html files aren't being deleted, then they're not being matched by the pattern you described - perhaps give us some actual examples?

---

### Post by sudodus on 2013-03-16
> **gefalu2008 said:**
> Thanks for the words of wardning. I have taken precautions - there is an up to date safety copy of my home folder. 

I think we are close now. The htm/html names contain empty spaces. The code seems to be trying to delete each word of the file names separately. I shall also test the interesting suggestion by Steeldriver.

```
for i in $(sudo find ~ -name "*_files*"|sed s/_files.*/*.htm*/); do echo rm [COLOR=#ff0000]"$i"[/COLOR]; done
```
If you enclose the placeholder in double quotes (") it should remove names with spaces. I tried it in my computer, and it worked for me. But notice that this script assumes that the folders "_files" are used and need to be there. Otherwise you need to use the info from the file 'folders.txt', as described by *steeldriver*.

But you are close now :-)

---

### Post by gefalu2008 on 2013-03-16
When running 

while read -r -d $'\0' dir; do echo rm "${dir%_files}".html && echo rmdir "$dir"; done < <(find . -type d -name '*_files' -print0)

I discovered that the folders were left intact simply because they were not empty. Html files were eliminated if there was only one html file to be eliminated in a directory. So this solution cannot be very far from the mark either.

---

### Post by steeldriver on 2013-03-16
... yes my apologies, I was stuck in the original mindset that you wanted to empty the dir (remove an htm file *inside* it) then remove it - just replace rmdir with the recursive rm as noted above

---

### Post by sudodus on 2013-03-16
When the htm and html files at the same level as the "*_files*" directories are removed, you can run this command to get rid of the "*_files*" directories. The -ri means recurse and interactive, so you can select interactively to keep or wipe a file. If you want to wipe everything, remove the red **[COLOR=#ff0000]i[/COLOR]**.

```
for i in $(sudo find ~ -name "*_files*"); do rm -r**[COLOR=#ff0000]i[/COLOR]** "$i"; done
```

---

### Post by gefalu2008 on 2013-03-16
Thank you both! It is amazing what you can do when you have about 100 times the beans I have.  I'll have to take a weekend break here.

---

### Post by sudodus on 2013-03-16
Have a nice week-end both of you :-)

---

### Post by schragge on 2013-03-16
It may be helpful if you describe how those files and directories were created in the first place. I imagine you were using some tool to retrieve content of web sites for offline use that creates hierarchies like
```

example.com_index.html
example.com_files/
example.com_files/main.css
example.com_files/main.js
example.com_files/logo.png

```Am I right?

---

### Post by gefalu2008 on 2013-03-17
schragge,

thanks for joining the effort.

Some years ago I used to save interesting Internet pages by the menu route File->Save as ...
This produced both the folders and htm files of the type

example.com_files
example.com_index.html
or example.com_index.htm

where images and other stuff are in the "example.com_files" folder. 

Now these files and folders are outdated and should be deleted.

My home folder also contains some lone htm/html files that have
no associated folder with the same name. These files, too, are
located in various directories. These lone files must not
be deleted, but that should not be a problem if the purge is 
carried out by using the "_files" folders as a starting point.

I have a laptop on which I can test suggestions in a relatively
safe way.

Thanks again for considering my problem.

---

### Post by gefalu2008 on 2013-03-17
For me the best solution was

```
while read -r dir; do rm "${dir%_files}".html && rm -rf "$dir"; done < folders.txt
```

So with this piece of code I was able to purge 900+ folders & files on the basis of folders
listed in the folders.txt. Steeldriver, thank you very much!

I especially liked the opportunity to use the folders.txt list, as it provided feedback on how I was
doing.

I am intrigued by the expression "${dir%_files}".html  - if you have time, please explain how it works. 
Or where can I find more information on this structure.

Sudodus also, thanks very much for your prompt and helpful action!

---

### Post by steeldriver on 2013-03-17
Glad that worked for you

```
${dir%_files}
```
is a bash parameter substitution - it says "remove any trailing portion of *dir* that matches *_files*" - so that gives you the basename, then you can add .html to get the html filename corresponding to the dir. The quotes are just good practice to prevent the filename getting split at spaces.

You can read about it all here -->  [http://tldp.org/LDP/abs/html/parameter-substitution.html](http://tldp.org/LDP/abs/html/parameter-substitution.html) 

It's basically a way of doing variable substitutions natively in the shell - instead of using an external program like 'sed' as another poster suggested

---

### Post by gefalu2008 on 2013-03-18
Thank you - it is so clear
(when somebody explains it).

---

