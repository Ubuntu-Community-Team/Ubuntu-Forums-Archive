---
title: "Case insensitivity in a for loop using a variable"
date: 2012-10-13
forum: Programming Talk
---

### Post by jamesisin on 2012-10-13
I am working to update one of my scripts:

[Recursive Prepending Script]("http://jamesisin.com/a_high-tech_blech/index.php/2011/04/recursive-prepending-script/")

I was using a fixed file extension and that was pretty easy to deal with in terms of accounting for variable cases (by using [Ff] &c within the loop).

However, I'm trying to allow the user to select the file extension.  This is the relevant section with my latest (failed) attempt:

```
      # set case insensitivity
      shopt -s nocasematch
      
      # change file names in sub folder
      
      for filepath in "/$discpath/$disc/"*.$fileextension; do
         filename=$( basename "$filepath" ) 
         mv "$discpath/$disc/$filename" "$discpath/$disc.$filename"
         echo $filename changed
      done
      
      # unset case insensitivity
      shopt -u nocasematch

```

If the case doesn't match (between the user-supplied $fileextension and the for-generated $filename) it throws an error about not finding the file.

I think one of the things causing difficulty is I'm dealing with two case insensitivities: one in the variable and one in the file names.  I don't want the script to care whether the user-submitted file extension is caps or not and I don't want the script to care whether the files it's looking at are in any particular case either.

Suggestions?

---

### Post by jamesisin on 2012-10-13
Here is the error which it throws:

```
mv: cannot stat `/home/[username]/Music/Raw Fiddle [mp3] [320]/01/*.MP3': No such file or directory
*.MP3 changed
mv: cannot stat `/home/[username]/Music/Raw Fiddle [mp3] [320]/02/*.MP3': No such file or directory
*.MP3 changed

```

So, it's not finding the files which tells me shopt isn't effecting the for loop.

(I used capital MP3 because I know the files have mp3.)

---

### Post by jamesisin on 2012-10-13
Thanks anyway.  I switched from nocasematch to nocaseglob and it works now.  You'll be able to find the new script through my blog at the link in the original post.

---

