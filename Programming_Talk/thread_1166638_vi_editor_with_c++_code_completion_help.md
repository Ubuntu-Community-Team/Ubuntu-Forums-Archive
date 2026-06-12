---
title: "vi editor with c++ code completion help"
date: 2009-05-21
forum: Programming Talk
---

### Post by colau on 2009-05-21
Hello
Someone please tell the procedure how get the c++ code completion in vi editor.
Following this 
[http://www.vim.org/scripts/script.php?script_id=1213](http://www.vim.org/scripts/script.php?script_id=1213)
but it is not working if i do vv.p then "CTRL + P" the pushback() funcion does not appear.
```

#include<stdio.h>
#include<vector>
#include<stack>
#include<iostream>
using namespace std;
int main(){
        stack<int>st;
        vector<int>vv;
        vv.p
        pritnf("shibly");
        return 0;
}

```

---

### Post by ad_267 on 2009-05-22
I haven't seen that before. There's [omni completion]("http://vim.wikia.com/wiki/Omni_completion") as well as an article [here]("http://arstechnica.com/open-source/guides/2009/05/vim-made-easy-how-to-get-your-favorite-ide-features-in-vim.ars") which might be more useful.

---

### Post by colau on 2009-05-22
> **ad_267 said:**
> I haven't seen that before. There's [omni completion]("http://vim.wikia.com/wiki/Omni_completion") as well as an article [here]("http://arstechnica.com/open-source/guides/2009/05/vim-made-easy-how-to-get-your-favorite-ide-features-in-vim.ars") which might be more useful.
Confusion.
In $HOME, is there any directory named ".vim" and a file named ".vimrc" by default after vim installation?
I had to create those.

---

### Post by ad_267 on 2009-05-22
> **colau said:**
> Confusion.
In $HOME, is there any directory named ".vim" and a file named ".vimrc" by default after vim installation?
I had to create those.

No, those aren't created, you have to create them yourself. The default vimrc for all users is in /etc/vim/.

---

### Post by colau on 2009-05-22
> **ad_267 said:**
> No, those aren't created, you have to create them yourself. The default vimrc for all users is in /etc/vim/.
Thanks.

Here [http://vim.wikia.com/wiki/VimTip1608](http://vim.wikia.com/wiki/VimTip1608) the first point is 

1. Install OmniCppComplete. See its doc/omnicppcomplete.txt file for information. 

What does it mean by install OmniCppComplete?
Does "install OmniCppComplete" mean just to extract the files in ~/.vim directory?
[http://www.vim.org/scripts/script.php?script_id=1520](http://www.vim.org/scripts/script.php?script_id=1520)

---

### Post by ad_267 on 2009-05-22
It looks like there's a few more steps:

2) In vim enter :helptags $HOME/.vim/doc 
3) Type :h omnicppcomplete and please read the installation paragraph.

---

### Post by colau on 2009-05-22
> **ad_267 said:**
> It looks like there's a few more steps:

2) In vim enter :helptags $HOME/.vim/doc 
3) Type :h omnicppcomplete and please read the installation paragraph.
Would you please tell what does this command do?
```

helptags $HOME/.vim/doc

```
I typed this command in vi editor but it seems that nothing happens.

---

### Post by ad_267 on 2009-05-22
I don't think it's supposed to give any output, it's just building a list of tags.
```
:helpt[ags] [++t] {dir}

Generate the help tags file(s) for directory {dir}.
All "*.txt" and "*.??x" files in the directory are
scanned for a help tag definition in between stars.
The "*.??x" files are for translated docs, they
generate the "tags-??" file, see |help-translated|.
The generated tags files are sorted.
When there are duplicates an error message is given.
An existing tags file is silently overwritten.
The optional "++t" argument forces adding the
"help-tags" tag.  This is also done when the {dir} is
equal to $VIMRUNTIME/doc.
To rebuild the help tags in the runtime directory
(requires write permission there):
:helptags $VIMRUNTIME/doc
{not in Vi}

```

---

### Post by colau on 2009-05-22
```

3. Installation~
                                                *omnicpp-installation*
3.1. Script installation~

Unzip the downloaded file in your personal |vimfiles| directory (~/.vim under 
unix or %HOMEPATH%\vimfiles under windows). The 'omnifunc' will be 
automatically set for C and C++ files.

You also have to enable plugins by adding these two lines in your|.vimrc|file: >

        set nocp
        filetype plugin on
<
Please see |cp| and |filetype-plugin-on| sections for more details.

3.1.1. Files~

After installation you should find these files :

    after\ftplugin\cpp.vim
    after\ftplugin\c.vim

    autoload\omni\common\debug.vim
                        \utils.vim

    autoload\omni\cpp\complete.vim
                     \includes.vim
                     \items.vim
                     \maycomplete.vim
                     \namespaces.vim
                     \settings.vim
                     \tokenizer.vim
                     \utils.vim

    doc\omnicppcomplete.txt

3.2. Building the Exuberant Ctags database~

To extract C/C++ symbols information, the script needs an |Exuberant_ctags|
database.

You have to build your database with at least the following options:
        --c++-kinds=+p  : Adds prototypes in the database for C/C++ files.
        --fields=+iaS   : Adds inheritance (i), access (a) and function 
                          signatures (S) information.
        --extra=+q      : Adds context to the tag name. Note: Without this
                          option, the script cannot get class members.

Thus to build recursively a ctags database from the current directory, the
command looks like this:
>
        ctags -R --c++-kinds=+p --fields=+iaS --extra=+q .

```
Can you tell what would be nocp,filetype,plugin there?
```

set nocp
filetype plugin on

```

---

### Post by colau on 2009-05-22
> **ad_267 said:**
> I don't think it's supposed to give any output, it's just building a list of tags.
```
:helpt[ags] [++t] {dir}

Generate the help tags file(s) for directory {dir}.
All "*.txt" and "*.??x" files in the directory are
scanned for a help tag definition in between stars.
The "*.??x" files are for translated docs, they
generate the "tags-??" file, see |help-translated|.
The generated tags files are sorted.
When there are duplicates an error message is given.
An existing tags file is silently overwritten.
The optional "++t" argument forces adding the
"help-tags" tag.  This is also done when the {dir} is
equal to $VIMRUNTIME/doc.
To rebuild the help tags in the runtime directory
(requires write permission there):
:helptags $VIMRUNTIME/doc
{not in Vi}

```

Finally vim works with code completion.
Thanks.

---

