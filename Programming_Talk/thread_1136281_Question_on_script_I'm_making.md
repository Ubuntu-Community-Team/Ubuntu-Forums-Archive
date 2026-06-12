---
title: "Question on script I'm making"
date: 2009-04-24
forum: Programming Talk
---

### Post by brandon88tube on 2009-04-24
I'm trying to make a script that I can send files to, have it return the value and then delete the file. I'm not that great at writing scripts as I have only done it once. I need to know if something like this would work and please correct the syntax if I have it wrong.
```
function fldel ($file){
	return $file;
	rm $file;
	exit;
}
```

EDIT: Forgot to mention that this is supposed to be a script like bash or something.

---

### Post by Mateo on 2009-04-24
return is always the last line in a function.

---

### Post by brandon88tube on 2009-04-24
Is this even correct though? I'm going to just be sending a file directly to the script. Do I need anything else or is this fine?

---

### Post by croto on 2009-04-25
hey man, what do you mean by "return the value"? what would you like the script to do besides removing the file?

---

### Post by brandon88tube on 2009-04-25
I'm not even sure if a bash script is capable of doing this. I want to send a file directly to the script, have the script send back the file contents and then remove that file. Essentially I'm trying to create a file exactly like the /dev/null file in that its just deletes the file, but instead of returning NULL I want it to return the file contents. Should this be asked elsewhere?

---

### Post by Saint Angeles on 2009-04-25
im not an expert in BASH, but couldnt you use cat to display the contents?

like:
```
function fldel (FILE){
     cat $FILE;
     rm -f $FILE;
     exit;
}
```

this is wrong.... i'm doing some research on this and i'll post the correct answer when i figure it out.

---

### Post by brandon88tube on 2009-04-25
Truthfully I have no idea. I don't think I script is going to make what I want. I want to symlink a folder location to the file as if it were /dev/null that is why I keep bringing that up. I want to send files to this symlink which would end up going to my file/script I created.

---

