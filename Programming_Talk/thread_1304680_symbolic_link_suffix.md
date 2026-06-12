---
title: "symbolic link suffix"
date: 2009-10-29
forum: Programming Talk
---

### Post by osx on 2009-10-29
I've read the man page for the "ln" command and read there is an option that will not overwrite a symbolic link if one of the same name already exists.

For example, if I already have a symbolic link called "myfile.txt" and attempt to create another one, there is an option for making a backup of the existing link file without overwriting it (i.e., I would now have a link called myfile.txt and one called myfile.txt.~1~). To me, this seemed ideal for a simple shell script I am writing for scanning directories for audio and video files and creating symbolic links to them.

The problem I ran into, however, is that the backup symbolic links are hidden. I assume this is because of the tildes (i.e., the ~ character) in the name. Before this I thought only files beginning with a period were hidden.

I attempted to use the suffix option with "ln" so that it would not use a tilde in hopes of making visible symbolic links; however, nothing I have tried has worked. I keep ending up with backup filenames that contain a tilde.

Here is an example of what I have tried to change the suffix from ~ to something like #.

```
ln --backup=numbered --suffix=# -s /media/shared/uupc_s02e16_high.ogg
```

With this command, I still end up with a symbolic link of uupc_s02e16_high.ogg~1~ when an existing symbolic link to the file already exists. I would rather have a suffix that does not make the link hidden. I'm not particular on what the suffix is, just as long as it does not make the link hidden.

I've tried other characters for the suffix besides #, but still end up with the tildes.

Any help is appreciated.

Thanks.

---

### Post by Arndt on 2009-10-29
> **osx said:**
> I've read the man page for the "ln" command and read there is an option that will not overwrite a symbolic link if one of the same name already exists.

For example, if I already have a symbolic link called "myfile.txt" and attempt to create another one, there is an option for making a backup of the existing link file without overwriting it (i.e., I would now have a link called myfile.txt and one called myfile.txt.~1~). To me, this seemed ideal for a simple shell script I am writing for scanning directories for audio and video files and creating symbolic links to them.

The problem I ran into, however, is that the backup symbolic links are hidden. I assume this is because of the tildes (i.e., the ~ character) in the name. Before this I thought only files beginning with a period were hidden.

I attempted to use the suffix option with "ln" so that it would not use a tilde in hopes of making visible symbolic links; however, nothing I have tried has worked. I keep ending up with backup filenames that contain a tilde.

Here is an example of what I have tried to change the suffix from ~ to something like #.

```
ln --backup=numbered --suffix=# -s /media/shared/uupc_s02e16_high.ogg
```

With this command, I still end up with a symbolic link of uupc_s02e16_high.ogg~1~ when an existing symbolic link to the file already exists. I would rather have a suffix that does not make the link hidden. I'm not particular on what the suffix is, just as long as it does not make the link hidden.

I've tried other characters for the suffix besides #, but still end up with the tildes.

Any help is appreciated.

Thanks.

Do you mean hidden in Nautilus? They are not hidden by 'ls'. In Nautilus, you can set the preferences to show hidden files.

---

### Post by osx on 2009-10-29
> **Arndt said:**
> Do you mean hidden in Nautilus? They are not hidden by 'ls'. In Nautilus, you can set the preferences to show hidden files.

Correct, I mean they are not visible in Nautilus because it does not display hidden files by default. The "ls -a" option will show them, but I want to be able to see them without having to set Nautilus to show hidden files. That's why I want to change the suffix to something that will not make the links "hidden".

Thanks.

---

### Post by Arndt on 2009-10-29
> **osx said:**
> Correct, I mean they are not visible in Nautilus because it does not display hidden files by default. The "ls -a" option will show them, but I want to be able to see them without having to set Nautilus to show hidden files. That's why I want to change the suffix to something that will not make the links "hidden".

Thanks.

Maybe there is an option somewhere in Nautilus not to treat that suffix as hidden - I don't know.

---

### Post by osx on 2010-06-30
I'm still needing to resolve this issue. I've been trying a number of different things without success. Anybody have some new suggestions?

---

### Post by geirha on 2010-06-30
You could use a function like this. It first tries to create the link. If that fails, it checks if linkname.1 exists, then linkname.2 etc, until it finds an available one, linkname.i, then moves linkname to linkname.i and tries to create the link again.

Obviously, if you simultaneously run more than one of this function on the same link, it will likely overwrite one, but I doubt you'll be doing that anyway.
```
myln () 
{
    local i=1
    if (( $# != 2 )); then
        echo "Usage: $FUNCNAME TARGET LINK_NAME" >&2
        return 1
    fi
    if ! ln -s "$1" "$2" 2>/dev/null; then
        while [[ -e $2.$i || -L $2.$i ]]; do
            ((i++))
        done
        mv "$2" "$2.$i" && ln -s "$1" "$2"
    fi
}

```

You can put that at the bottom of ~/.bashrc and then, after starting a new shell, you can do  ```
myln foo bar
# instead of
ln -s foo bar
```

---

