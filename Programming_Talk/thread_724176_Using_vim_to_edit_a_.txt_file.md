---
title: "Using vim to edit a .txt file"
date: 2008-03-14
forum: Programming Talk
---

### Post by thelugnut on 2008-03-14
I am just starting to learn "Vim" and am trying to run the vimtutor.

I got to this section:\
>  Lesson 1.6: EDITING A FILE


                    ** Use  :wq  to save a file and exit. **

  !! NOTE: Before executing any of the steps below, read this entire lesson!!

  1. Exit this tutor as you did in lesson 1.2:  :q!

  2. At the shell prompt type this command:  vim tutor <ENTER>
     'vim' is the command to start the Vim editor, 'tutor' is the name of the
     file you wish to edit.  Use a file that may be changed.

  3. Insert and delete text as you learned in the previous lessons.

  4. Save the file with changes and exit Vim with:  :wq  <ENTER>

  5. Restart the vimtutor and move down to the following summary.

  6. After reading the above steps and understanding them: do it.


Here I am stuck. 

I wrote a small text file and put it in various places but each time I try to run "vim <filename.txt>,  Vim said it was a "new file".

The file is presently residing in /usr/bin.

So how do I get vim to recognize the file and open for me to edit it?

Can someone help me over this stumbling block, please?

---

### Post by Keith Hedger on 2008-03-14
use the full path to the file ie ```
vim /usr/bin/filename.txt
```

---

### Post by jken146 on 2008-03-14
I wouldn't put the file in /usr/bin.  You'll run into permission problems if it isn't in you home directory.

---

### Post by thelugnut on 2008-03-14
Thank you for the quick responses.

O.K. I moved the file to my Home directory and tried again. No problem! It came right up and I edited the heck out of that little file.:guitar:

I thought it was necessary to put the file in the /usr/bin but I haven't a clue as to where I got that idea. I must have read something incorrectly. (again) :confused:

Again, thanks for the replies. I ready to plod on. ):P

---

