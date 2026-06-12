---
title: "HOWTO: Auto-complete ctags when using vim in bash"
date: 2008-04-17
forum: Programming Talk
---

### Post by SeanHodges on 2008-04-17
For anyone else who uses vim and ctags, I've written a small auto-completer function for bash. Add the following into your ~/.bash_completion file (create it if it does not exist):

Thanks go to stylishpants for his many fixes and improvements.

```


_vim_ctags() {
    local cur prev

    COMPREPLY=()
    cur="${COMP_WORDS[COMP_CWORD]}"
    prev="${COMP_WORDS[COMP_CWORD-1]}"

    case "${prev}" in
        -t)
            # Avoid the complaint message when no tags file exists
            if [ ! -r ./tags ]
            then
                return
            fi

            # Escape slashes to avoid confusing awk 
            cur=${cur////\\/}

            COMPREPLY=( $(compgen -W "`awk -vORS=" "  "/^${cur}/ { print \\$1 }" tags`" ) )
            ;;
        *)  
            _filedir_xspec
            ;;
    esac    
}   

# Files matching this pattern are excluded
excludelist='*.@(o|O|so|SO|so.!(conf)|SO.!(CONF)|a|A|rpm|RPM|deb|DEB|gif|GIF|jp?(e)g|JP?(E)G|mp3|MP3|mp?(e)g|MP?(E)G|avi|AVI|asf|ASF|ogg|OGG|class|CLASS)'

complete -F _vim_ctags -f -X "${excludelist}" vi vim gvim rvim view rview rgvim rgview gview
```

Once you restart your bash session (or create a new one) you can type:

```

~$ vim -t MyC<tab key>
```

and it will auto-complete the tag the same way it does for files and directories:

```

MyClass MyClassFactory
~$ vim -t MyC
```

I find it really useful when I'm jumping into a quick bug fix...

---

### Post by stylishpants on 2008-04-17
Thanks, good idea!

A couple of problems though.

First, it's too slow for my slow computer and large source tree.  My tags file is 45K lines, which all get filtered by compgen when <tab> is hit.  A typical string takes over 30 seconds to complete.  I changed your code a bit to speed it up by pre-filtering the tags in awk before compgen sees them, this makes it usable for me.  Strings now typically take under 1 second to complete.

Second, this has some quirks.  
If you try to complete a filename like this:
dir1/dir2/file.txt
You'll find that it completes the dir name and appends a space, which means you have to backspace before you can complete on filenames within that dir.
Also, normally tab completion for vim (as provided by the bash-completion package) will ignore many binary files like *.o *.so *.ogg and so on, this is lost with this configuration.

I addressed this by copying bash-completion's default handling for vim into your 'complete' command.

```

_vim_ctags() {
    local cur prev
    COMPREPLY=()
    cur="${COMP_WORDS[COMP_CWORD]}"
    prev="${COMP_WORDS[COMP_CWORD-1]}"
        
    # Avoid the complaint message when no tags file exists
    if [ ! -r ./tags ]
    then
        return
    fi

    case "${prev}" in
        -t) 
            COMPREPLY=( $(compgen -W "`awk -vORS=\" \"  "/^${cur}/ { print \\$1 }" tags`" -- ${cur}) )
            ;;
        *)
            ;;
    esac
}

complete -F _vim_ctags -f -X '*.@(o|so|so.!(conf)|a|rpm|gif|GIF|jp?(e)g|JP?(E)G|mp3|MP3|mp?(e)g|MPG|avi|AVI|asf|ASF|ogg|OGG|class|CLASS)' vi vim gvim rvim view rview rgvim rgview gview


```

---

### Post by SeanHodges on 2008-04-21
Thanks for your suggestions stylishpants! 

I've applied them to the parent post. I also moved the tags file check into the select condition so it only checks when completing tags.

---

### Post by stylishpants on 2008-04-23
Good idea splitting out the exclude list, but as it is currently posted there are some problems with that.

First, the exclude list is declared local to the shell function, but is only used outside the function.  Of course, when used outside the function, it expands to nothing, which is broken. 

Secondly, there appear to be some quoting problems with the exclude list too, because even with the exclude string moved outside the function, it still doesn't actually work as posted.  When in my source tree I do
```
vim libs/<tab>
```
I'm still seeing my object files (*.o) along with my source files.

Third, I get an awk error when use the -t flag but try to complete a filename.  I realize this is not the intended use of the -t flag, but it happens and it's bad form to let it crash the completion command.  I totally missed this in my earlier post.

Here's an updated version which fixes all the above issues:


```

_vim_ctags() {
    local cur prev

    COMPREPLY=()
    cur="${COMP_WORDS[COMP_CWORD]}"
    prev="${COMP_WORDS[COMP_CWORD-1]}"

    case "${prev}" in
        -t)
            # Avoid the complaint message when no tags file exists
            if [ ! -r ./tags ]
            then
                return
            fi

            # Escape slashes to avoid confusing awk 
            # (eg. without this, if $cur contains slashes (eg. "./dir/path"), the awk command /^${cur}/
            # could expand to /^./dir/path/, which is a syntax error.)
            # For an explanation of this command:  man bash | less -p 'Parameter Expansion'  
            cur=${cur////\\/}

            COMPREPLY=( $(compgen -W "`awk -vORS=" "  "/^${cur}/ { print \\$1 }" tags`" ) )
            ;;
        *)  
            _filedir_xspec
            ;;
    esac    
}   

# Files matching this pattern are excluded
excludelist='*.@(o|O|so|SO|so.!(conf)|SO.!(CONF)|a|A|rpm|RPM|deb|DEB|gif|GIF|jp?(e)g|JP?(E)G|mp3|MP3|mp?(e)g|MP?(E)G|avi|AVI|asf|ASF|ogg|OGG|class|CLASS)'

complete -F _vim_ctags -f -X "${excludelist}" vi vim gvim rvim view rview rgvim rgview gview


```

---

### Post by SeanHodges on 2008-04-28
Great! I've amended the parent post and my own copy. Thanks again!

---

### Post by SeanHodges on 2008-04-28
I've added the script to the Vim wiki: [http://vim.wikia.com/wiki/Using_bash_completion_with_ctags_and_Vim](http://vim.wikia.com/wiki/Using_bash_completion_with_ctags_and_Vim)

---

