---
title: "get number of lines in a text file c/c++"
date: 2009-02-01
forum: Programming Talk
---

### Post by monkeyking on 2009-02-01
quite a few times I have to count the number of lines in a textfile.
And I always end up with something like

[PHP]
while(!.eof()){
  .getline(...);
  numLines1++;
}
return numLines;
[/PHP]

This of cause works. But It annoys me that I have to read in all lines of a file. Does anyknow know of a simpler or more beautifull way.

thanks in advance.

---

### Post by Nemooo on 2009-02-02
I don't know if this is faster. Basically it's just counting the number of characters until it reaches EOF.

```
int line_num(char *filename)
{
	FILE *f;
	char c;
	int lines = 0;

	f = fopen(filename, "r");

	if(f == NULL)
		return 0;

	while((c = fgetc(f)) != EOF)
		if(c == '\n')
			lines++;

	fclose(f);

	if(c != '\n')
		lines++;

	return lines;
}
```

---

### Post by Krupski on 2009-02-02
> **monkeyking said:**
> quite a few times I have to count the number of lines in a textfile.
And I always end up with something like

[PHP]
while(!.eof()){
  .getline(...);
  numLines1++;
}
return numLines;
[/PHP]

This of cause works. But It annoys me that I have to read in all lines of a file. Does anyknow know of a simpler or more beautifull way.

thanks in advance.

Honestly, I don't think there IS any way to tell how many lines a file has other than by counting them all.

Be careful though... DOS/Windows files with CR/LF endings, UNIX files with LF-only endings and MAC files with CR-only endings can confuse functions like getline() or fgets(), so be sure you make accommodations for those variations. 

-- Roger

---

