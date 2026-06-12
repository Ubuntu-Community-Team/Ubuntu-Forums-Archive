---
title: "renaming files in lots of folders"
date: 2011-10-22
forum: New to Ubuntu
---

### Post by Roger Allott on 2011-10-22
I have over a thousand folders in my Pictures folder and each of these sub-folders contains betweeen 1 and 100 image files.

Most of the image files end in ".jpg" as one would expect, but there are some errant ones that are named ".jpeg", ".JPG" or even ".JPEG".

If all of my image files were simply in the Pictures folder, renaming them to the ".jpg" suffix would be easy:
```
rename.ul .jpeg .jpg *.jpeg
```

and variations on that to cover the other two situations.

But because they're organised into folders, I'm a bit stumped. What command would do what I want to the files in all of the sub-folders of the Pictures folder?

Is it as simple as adding "-R" after the "rename.ul"?

---

### Post by enkay009 on 2011-10-22
I don't have much experience with rename.ul but you could use find.

find has an option that allows you to run a command on every file it finds.

Here's an example of using find to do an ls on each file found.

```
find /path/to/search/from -type f -exec ls {} \;
```

When you run this, find will pass each file it found as an argument to ls with {}. You should be able to adapt this example for rename.ul.

Try it out with some no destructive commands like echo or stat to get a better feel for find.

---

### Post by btindie on 2011-10-22
All of those are valid extensions, if anything I'd say .jpeg is the correct one as .jpg is more of a throw back to the windows days when it could only handle extensions of 3 characters. But that's by the by.

To answer your question you can do that with the find command.
```
find Pictures/ -type f \( -name '*.jpeg' -o -name '*.JPEG' -o -name '*.JPG' \) \
-exec sh -c "file='{}'; mv \"\$file\" \"\${file%.*}\".jpg" \; 
```Add the word 'echo ' in front of 'mv' if you want to see what files will be affected by the command.

---

### Post by egalvan on 2011-10-22
Typed in "file rename" in Synaptic,
and found this little gem...

> PrefixSuffix
PrefixSuffix is a GUI application that renames batches of files by
changing the beginning or end of their names.


it has a "recurse folders" option...
it may be useful to you..

---

### Post by papibe on 2011-10-22
```
find Pictures/ -iname '*.jpeg' -exec rename.ul .jpeg .jpg '{}' \;

```
This is what is does:
- Starts at Pictures/ and looks in all the tree structure under it.
- Match any file ending in .jpeg, case insensitive (-iname '*.jpeg')
- For each match execute a rename.

I hope it helps,
Regards.

---

### Post by Roger Allott on 2011-10-22
> **egalvan said:**
> Typed in "file rename" in Synaptic,
and found this little gem...



it has a "recurse folders" option...
it may be useful to you..

I've been looking for something like that for ages! Thanks.

There's a freeware utility for Windows that's very good for bulk renaming, called "Bulk Rename Utility". It's quite a bit more sophisticated than PrefixSuffix but hopefully the chaps who develop the latter will move towards the usability of the former.

---

### Post by Roger Allott on 2011-10-22
> **btindie said:**
> All of those are valid extensions, if anything I'd say .jpeg is the correct one as .jpg is more of a throw back to the windows days when it could only handle extensions of 3 characters. But that's by the by.


It's true that they're all valid image file extensions, but there are a number of web tools for selecting image files that refuse to recognise a file as an acceptable type unless it has .jpg as the suffix. It's nothing more than the web developer being a bit of a bozo when it comes to knowledge of file types, but you'd have thought he'd be sensible enough to find out before writing his code.

---

### Post by Roger Allott on 2011-10-22
Sadly, the PrefixSuffix GUI thing didn't work. Even when I had 'recurse folders' checked, it would only action the files in the folder and not those in sub-folders.

Using the CLI that has been suggested hasn't quite worked either. Changing a file suffixed .jpeg to one suffixed .jpg seems to be easy, but getting changes to files currently suffixed .JPG is proving to be far more difficult.

The mv based command sends me back this sort of error message:
```
mv: `Pictures/2775/2775-38.JPG' and `Pictures/2775/2775-38.jpg' are the same file
```

The rename based command, amended to get rid of case insensitivity by deleting the '-iname' bit, gives me:
```
find: ‘*.JPG’: No such file or directory
```
after a jolly long time of thinking about doing something.

---

### Post by gsmanners on 2011-10-22
> **Roger Allott said:**
> The mv based command sends me back this sort of error message:
```
mv: `Pictures/2775/2775-38.JPG' and `Pictures/2775/2775-38.jpg' are the same file
```

Ah, yes. That bug.

You need to rename .JPG to something like .TMP, then back to .jpg.

---

