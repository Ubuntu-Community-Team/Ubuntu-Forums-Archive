---
title: "cd into dir if and only if a dir exists"
date: 2012-02-11
forum: Programming Talk
---

### Post by larzconwell on 2012-02-11
Okay I'm creating a compile script and I want it to automatically untar it into a dir I create then cd into that dir. But when it untars' there might be a dir OR the source code. It just depends on the dev I guess. So how would I go about cd-ing into a dir if and only if that dir exists, otherwise try to compile.

```

compile_source() {
	if [[ "$pm" == "source" ]]; then
		mkdir compile && tar xzf "$1" -C compile/ && cd compile | echo -e "==> Extracting file and cd-ing into it...\n"
		if [[ #dir exists ]]; then
			# if there is only a directory cd into it otherwise try to compile
		fi
	else
		echo "This package should be available from your package manager..."
	fi
}

```

That's what I have so far..

---

### Post by savanna on 2012-02-11
MYDIR="~/foo"
if [ -d "$MYDIR" ] ; then
    cd "$MYDIR"
    ...
    ...
fi

---

### Post by larzconwell on 2012-02-11
That would work, but I won't know the name of the folder... if there's a folder.

---

### Post by savanna on 2012-02-11
There's probably more elegant ways to do this, but...

if ls -l | grep -q '^d' ; then
mydir=`ls -l | grep '^d' | head -1 | awk '{print $8}'`
..
..
fi

---

### Post by larzconwell on 2012-02-11
I'll worry about elegance when I finish the complete script! Haha
Thanks for the help!! I will have to try it in the morning

---

### Post by sisco311 on 2012-02-11
Check out BashFAQ 004 (link in my signature).

I'd try something like:
```

shopt -s nullglob

files=(*)
if (( ${#files[@]} == 1 )) && [[ -d ${files[0]} ]]; then
    cd ${files[0]}
    ...
fi

```

---

### Post by erind on 2012-02-11
> **larzconwell said:**
> Okay I'm creating a compile script and I want it to automatically untar it into a dir I create then cd into that dir. But when it untars' there might be a dir OR the source code. It just depends on the dev I guess. So how would I go about cd-ing into a dir if and only if that dir exists, otherwise try to compile.
...
Another way using shell built-ins:

```
compile_source() {
    if [[ "$pm" == "source" ]]
     then
        mkdir compile && tar xzf "$1" -C compile/ && cd compile 
        echo -e "==> Extracting file and cd-ing into it...\n"

        [COLOR=Blue]first_dir="$( printf "%s" */ )"[/COLOR]
        if [ [COLOR=Blue]-d "${first_dir%%/*}"[/COLOR] ]
         then
            [COLOR=Blue]cd "${first_dir%%/*}" 
[/COLOR]            ## other actions here
        else
           ## otherwise try to compile
        fi
    else
        echo "This package should be available from your package manager..."
    fi
}
```

---

