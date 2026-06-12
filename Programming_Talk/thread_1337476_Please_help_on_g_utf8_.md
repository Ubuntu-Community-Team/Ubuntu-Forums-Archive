---
title: "Please help on g_utf8_*"
date: 2009-11-25
forum: Programming Talk
---

### Post by froggyswamp on 2009-11-25
Folks I'm trying for several hours to figure out how to do basic work with utf8 strings in C without any success.

Say I have the utf8 string "/home/fox/.config"
I need to get the string from the start till the last occurrence of "/", that is I need to get "/home/fox", how do I do that using g_utf8_* functions? Anyone please?

I read
[http://library.gnome.org/devel/glib/stable/glib-Unicode-Manipulation.html](http://library.gnome.org/devel/glib/stable/glib-Unicode-Manipulation.html)
but I still can't figure out, I'm coming from Java and I'm used to a (completely) different approach..

---

### Post by MindSz on 2009-11-25
I'm not really familiar with g_utf8 functions, but do have to use those? Whenever I do text-file manipulation I just use normal ASCII values. So I get a line of code using fgets, manipulate it as a char* (a string) and printf it out using either printf or fprintf.

---

### Post by froggyswamp on 2009-11-25
Unfortunately I have to treat it as utf8 cause the string _will_ contain non-english (russian, chinese) characters... anyone please?

---

### Post by Arndt on 2009-11-25
> **froggyswamp said:**
> Folks I'm trying for several hours to figure out how to do basic work with utf8 strings in C without any success.

Say I have the utf8 string "/home/fox/.config"
I need to get the string from the start till the last occurrence of "/", that is I need to get "/home/fox", how do I do that using g_utf8_* functions? Anyone please?

I read
[http://library.gnome.org/devel/glib/stable/glib-Unicode-Manipulation.html](http://library.gnome.org/devel/glib/stable/glib-Unicode-Manipulation.html)
but I still can't figure out, I'm coming from Java and I'm used to a (completely) different approach..

I thought I installed the correct package in order to try it out, but I still don't have a glib.h. How is it installed?

---

### Post by froggyswamp on 2009-11-25
When compiling one needs to specify on the command line "-lglib-2.0".
libgtk2.0-dev makes sure you have that installed.
and
echo `pkg-config --libs --cflags gtk+-2.0`
prints out the config elements.

---

### Post by LKjell on 2009-11-25
utf-8 is locale dependent. If your locale is not set to right it might give you gibberish output. Check first with ```
locale
``` in a terminal and look for LC_CTYPE is set to utf-8. If you use a terminal for input check if character encode is set to utf-8 too.

You can either store your utf-8 characters as char or as wchar_t does not really matter.

```
#include <stdio.h>
#include <stdlib.h>
#include <locale.h>


int main()
{
	char *str = setlocale(LC_CTYPE, "");
	if(str == NULL)
	{
		fprintf(stderr,"Error when setting locale,");
		return EXIT_FAILURE;
	}
	
	wchar_t *vowels = L"aeiouæøå";
	char * vow = "aeiouæøå";
	
	printf("%ls\n", vowels);
	printf("%s\n", vow);
	
	puts("Remember l and L. Very easily to miss.\nAnd check your locale to be utf-8 or you get gibberish too!");
	return EXIT_SUCCESS;
}
```

---

### Post by froggyswamp on 2009-11-26
Anyway, the question hasn't been answered.
No one can give an example on doing a str.substring(x,y) in C on a utf8 string?

To reiterate, how do I get a utf8 substring from another ( utf8 ) string in C?

---

### Post by LKjell on 2009-11-26
I think you need to understand how utf-8 characters are stored first.
Then you need to know what do you want to work with. char or wchar_t .
wchar_t is a bit more easier to work with but takes more space. Try to see what this code of chunk do. It is similiar to strchr function.

```
void split(wchar_t *str, wint_t delimiter)
{
	wchar_t **s = malloc(sizeof(wchar_t*));

	for(int i = 0; str[i] != L'\0'; i++)
	{
		if(str[i] == delimiter)
		{
			s[0] = &str[i];
			break;
		}
	}
	
	printf("%ls\n", s[0]);
	free(s);
}
```

---

