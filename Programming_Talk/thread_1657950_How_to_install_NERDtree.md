---
title: "How to install NERDtree?"
date: 2011-01-01
forum: Programming Talk
---

### Post by gmyuser on 2011-01-01
Similar thread [here]("http://ubuntuforums.org/showthread.php?p=10304784#post10304784").

What commands in unix can i use to download and unzip?

>> Unzip the archive into your ~/.vim directory.

I have searched the web and everyone just says unzip. Well the is fine for experts, but I am running ubuntu on virtual box and can't figure out how to do that. I also don't know how to download it to my virtual box installation. 

Can I  use curl with the address? Where can i find that address? The Nerdtree page has a download button (do I right click to get THAT address?). What exactly would i type on my server? And then it is still a zip file?

---

### Post by johncburr on 2011-06-22
For some reason, I have no ~/.vim directory.  apt-get put the executables in usr/bin and the rest of the software who knows where.  So where do I extract the files now?

---

### Post by johncburr on 2011-06-22
Found the solution.
For other newbies like myself here is what you do:
1) Make a .vim directory with by typing:

mkdir ~/.vim

2) Then let vim know where it is by running vim and enter the command:

:let $VIM = "~/.vim"

the :help stuff still doesn't work, but you can type :NERDTree and it launches the tree.  You can hit ? from in there to get help.

---

