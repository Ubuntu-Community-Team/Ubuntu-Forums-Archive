---
title: "GIMP batch problem"
date: 2012-03-05
forum: New to Ubuntu
---

### Post by handflinger on 2012-03-05
I am moderately new to Ubuntu and very new to GIMP.  I hope this is the right forum for this question.  

I tweaked an example script from [http://www.gimp.org/tutorials/Basic_Batch/](http://www.gimp.org/tutorials/Basic_Batch/) and am having a lot of trouble figuring out what is wrong.  I kept reducing the script to its more basic form til this toy script is all that is left.  GIMP seems to accomplish the task of copying one file to another location, but it issues a GLib-WARNING.  

How do I get rid of this warning?
```

GIMP 2.6.11
Ubuntu 11.04

file: ~/.gimp-2.6/scripts/one-file-save-as-other.scm
(define (one-file-save-as-other filename1
                filename2)
    (let* 
        ((image    (car (gimp-file-load RUN-NONINTERACTIVE filename1 filename1)))
         (drawable (car (gimp-image-get-active-layer image)))
        )
        (gimp-file-save       RUN-NONINTERACTIVE image drawable filename2 filename2)
        (gimp-image-delete image)  
    )
)

execution:
bluejay@D520:~$ gimp -i -b '(one-file-save-as-other "a.gif" "bat.gif")' -b '(gimp-quit 0)'

(gimp:6871): GLib-WARNING **: /build/buildd/glib2.0-2.28.6/./glib/goption.c:2132: ignoring no-arg, optional-arg or filename flags (8) on option of type 0
batch command executed successfully
```

---

