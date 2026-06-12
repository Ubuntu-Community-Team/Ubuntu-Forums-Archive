---
title: "Remove last part of a text line in a file"
date: 2011-01-25
forum: Programming Talk
---

### Post by bcooperizcool on 2011-01-25
How can I remove the last part of lines from a file?

my code that doesn't work

```

while read name; do
sed "s/$name.app$//" < fileone | sort | uniq > filetwo
done < filewiththingtoremove

```

As always, Thanks!

---

### Post by slavik on 2011-01-25
you also need to add .* to the part you want to remove, unless you don't want to wildcard stuff, can you give us a short example of text and what you are trying to do?

---

### Post by bcooperizcool on 2011-01-25
where do I need to add .*?

Example of file
```

/var/stash/Applications/245-234453-GFSD/Facebook.app
/var/stash/Applications/PSL-742343-NWIM/Text.app

```

Example of file that contains the stuff to remove
```

Facebook
Text

```

Example of hopeful output into new file
```

/var/stash/Applications/245-234453-GFSD
/var/stash/Applications/PSL-742343-NWIM

```

---

### Post by worksofcraft on 2011-01-25
Well if you don't mind compiling it...
[php]

// g++ pathsplit.cpp
#include <cstdio>

char *split_path(char *buf) {
	char *p, *name;
	p = name = buf;
	// scan command line for /
	while (*p) {
		if (*p == '/') name = p; // leave a marker on the last /
		++p;
	}
	if (name == buf) return NULL;
	*name++ = '\0'; // string terminator
	return name;
}

int main() {
	char buf[2020];
	while (fgets(buf, sizeof(buf), stdin)) {
		if (split_path(buf)) printf("%s\n", buf);
	}
	return 0;
}
[/php]

---

### Post by Vaphell on 2011-01-25
```
echo '/var/stash/Applications/245-234453-GFSD/Facebook.app' | **sed -r 's:/[^/]+app$::'**
```
output
```
/var/stash/Applications/245-234453-GFSD
```

'/', one-or-more non-slash chars, 'app', end of line in case you wonder, could be even reduced to /[^/]*$

---

### Post by bcooperizcool on 2011-01-25
Ehhhh....  its for an iphone.  I don't think it supports that.  :(  I found another way by recoding some of the big script  Thanks though!

---

### Post by kurum! on 2011-01-25
```

ruby -F'/' -ane 'BEGIN{f2=open("file2").read.split("\n")}; puts $F[0..-2].join("/") if f2.grep($F[-1].split(".")[0]).size>0 ' file


```

---

### Post by Arndt on 2011-01-26
> **worksofcraft said:**
> Well if you don't mind compiling it...
[php]

// g++ pathsplit.cpp
#include <cstdio>

char *split_path(char *buf) {
	char *p, *name;
	p = name = buf;
	// scan command line for /
	while (*p) {
		if (*p == '/') name = p; // leave a marker on the last /
		++p;
	}
	if (name == buf) return NULL;
	*name++ = '\0'; // string terminator
	return name;
}

int main() {
	char buf[2020];
	while (fgets(buf, sizeof(buf), stdin)) {
		if (split_path(buf)) printf("%s\n", buf);
	}
	return 0;
}
[/php]

You could probably use 'strrchr' somewhere here.

---

### Post by geirha on 2011-01-26
```
awk -F/ 'BEGIN{OFS=FS} NR==FNR{a[$0".app"];next} $NF in a {NF--} 1' filewiththingtoremove fileone > filetwo
```

---

