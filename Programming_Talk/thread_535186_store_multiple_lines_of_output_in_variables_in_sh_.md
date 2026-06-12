---
title: "store multiple lines of output in variables in sh script?"
date: 2007-08-26
forum: Programming Talk
---

### Post by Krijk on 2007-08-26
I wrote the following to create a list of new images since my last download from a digital camera. 

In order to do this I create a number of temporary files which are removed at the end of the script. The only file that has to exist as a file is the camera.latest.download.txt which stores the latest download filelist. 
The list_of_new_files_to_download.tmp contains the names of new files which are used as input in a download function later in the script.

I'm pretty new at scripting so I'm trying to improve it. The solution works, but isn't pretty. How can I store the output to variables and use these in the script so I won't need temporary files? 

```
#!/bin/sh
# selection from script
media='/path/to/camera/'

check_files_to_download()
{
	cd $media
	ls -l >/work/dir/files_on_camera.tmp
	cat /work/dir/files_on_camera.tmp | awk 'FNR>1 { print $0 }'>/work/dir/files_on_camera2.tmp
	cat /work/dir/camera.latest.download.txt | awk 'FNR>1 { print $0 }'>/work/dir/camera.latest.download.tmp
	comm -23 /work/dir/files_on_camera2.tmp /work/dir/camera.latest.download.tmp >/work/dir/newfiles.tmp
	cat /work/dir/newfiles.tmp | awk 'FNR>0 { print $8 }' >/work/dir/list_of_new_files_to_download.tmp 
}

check_files_to_download
```

---

### Post by cwaldbieser on 2007-08-26
You can put many commands in a single pipeline.  Also, in many instances, you do not need to use "cat".  I have also used process substitution which is just a way to take the output of a pipeline and treat it like a named file. The "comm" command wants 2 files as its arguments rather than an input stream.

```

#!/bin/sh
# selection from script
media='/path/to/camera/'

check_files_to_download()
{
	cd $media
	comm -23 <(ls -l | awk 'FNR>1 { print $0 }') <(awk 'FNR>1 { print $0 }' /work/dir/camera.latest.download.txt) | awk 'FNR>0 { print $8 }' >/work/dir/list_of_new_files_to_download.tmp 
}

check_files_to_download

```

If the process substitution is confusing, think of it like:
```

comm -23 <(output-from-pipeline-1) <(output-from-pipeline-2) > final-output-redirected-here

```

---

### Post by Krijk on 2007-08-26
Thanks for the suggestion. It is a lot shorter. 

It does however only seems to work in **bash**. When I try it in **sh** , it comments on the unexpected (

The comm also doesn't work with the whole line ( $0 ). Only with the file-name ( $8 ). When a file is removed in the beginning the compare fails and everything after the removed line is seen as new.
I would like to compare the file size too; just in case a old file-name is re-used by the camera.

What is an alternative compare I can use for this?

---

### Post by cwaldbieser on 2007-08-26
> **Krijk said:**
> Thanks for the suggestion. It is a lot shorter. 

It does however only seems to work in **bash**. When I try it in **sh** , it comments on the unexpected (

The comm also doesn't work with the whole line ( $0 ). Only with the file-name ( $8 ). When a file is removed in the beginning the compare fails and everything after the removed line is seen as new.
I would like to compare the file size too; just in case a old file-name is re-used by the camera.

What is an alternative compare I can use for this?

Yes, the standard bourne shell does not have process substitution.
You can get other file attributes with "stat".
You can compare files byte by byte with "cmp".  An exit value of 0 means the files are identical.

---

