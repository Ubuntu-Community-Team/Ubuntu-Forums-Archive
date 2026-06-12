---
title: "strcpy segfault"
date: 2013-01-23
forum: Programming Talk
---

### Post by Hairy_Palms on 2013-01-23
So if got some C code that keeps segfaulting, and i cant understand why, the problem line is here, gdb doesnt reveal anything, yet copying a new string works fine.
```
	validthemes = 0;
	for (n = 0; n < userdirlength; n++)
	{
		if (strcmp(userfolderarray[n], "Empty")!= 0){
			printf("%s\n",userfolderarray[n]);
			//line below works fine
			strcpy(themes_id[validthemes], "Why does this work but the other strcpy doesnt!");
			printf("%s\n",themes_id[validthemes]);
			//line below causes segfault
			strcpy(themes_id[validthemes], userfolderarray[n]);
			strcpy(themes_name[validthemes], userthemenamearray[n]);
			validthemes++;
		}
	}
```

A copy of most of the file so you can see where the array comes from, if anyone has a clue what the problem is id be incredibly grateful :)

```
#include <sys/types.h>
#include <dirent.h>
#include <regex.h>
#include <stdio.h>
#include <gtk/gtk.h>
#include <string.h>
#include <unistd.h>
#include <pwd.h>
#include <stdlib.h>
 
enum {
    WALK_OK = 0,
    WALK_BADPATTERN,
    WALK_BADOPEN,
};

static gchar *themes_id[100];
static gchar *themes_name[100];

int walk_directories(const char *dir, const char *pattern, gchar theme_folders[][100], gchar theme_names[][100])
{
    struct dirent *entry;
    regex_t reg;
    DIR *d; 
    int i = 0;
    char *tempdname;
    FILE *file;

    gchar *subdir = NULL;
    GKeyFile *theme_file = NULL;
    GError *error = NULL;

    theme_file = g_key_file_new ();

    if (regcomp(&reg, pattern, REG_EXTENDED | REG_NOSUB))
        return WALK_BADPATTERN;
    if (!(d = opendir(dir)))
        return WALK_BADOPEN;
    while (entry = readdir(d))
	{
        if (!regexec(&reg, entry->d_name, 0, NULL, 0) )
		tempdname = entry->d_name;
		if( entry->d_type == DT_DIR && strcmp(entry->d_name,".") != 0 && strcmp(entry->d_name,"..") != 0)
			{
				subdir = g_build_filename(dir, tempdname, "/index.theme", NULL);
				//printf("%i %s %s\n",i,subdir,(g_key_file_load_from_file (theme_file, subdir, G_KEY_FILE_NONE, &error))?"true":"false");
				if (g_key_file_load_from_file (theme_file, subdir, G_KEY_FILE_NONE, &error)){
					//g_print("%s\n",g_key_file_get_string (theme_file, "X-GNOME-Metatheme", "Name", NULL));
					if (g_key_file_get_string (theme_file, "X-GNOME-Metatheme", "Name", NULL) != NULL){
						g_strlcpy(theme_names[i], g_key_file_get_string (theme_file, "X-GNOME-Metatheme", "Name", NULL), 100);
						strcpy(theme_folders[i], (tempdname));
						i++;
					}
					else if (g_key_file_get_string (theme_file, "Desktop Entry", "Name", NULL) != NULL){
						g_strlcpy(theme_names[i], g_key_file_get_string (theme_file, "Desktop Entry", "Name", NULL), 100);
						strcpy(theme_folders[i], (tempdname));
						i++;
					}
				}
				else{
					g_strlcpy(theme_names[i], "Empty", 100);
					strcpy(theme_folders[i], "Empty");
					i++;
				}			
				g_free (subdir);
				error = NULL;
			}
	}
    g_key_file_free (theme_file);
    closedir(d);
    regfree(&reg);
    return WALK_OK;
}

int dir_length(char *aDir)
{
	DIR *dp;
	int i = 0;
	struct dirent *ep;
	dp = opendir (aDir);

	if (dp != NULL)
	{
		while (ep = readdir (dp))
			i++;
		(void) closedir (dp);
	}
	i--;
	i--;
	return i;
}

void populate_themes()
{
	int n = 0;
	int systemdirlength = 0;
	int validthemes = 0;
	int userdirlength = 0;

	struct passwd *pw = getpwuid(getuid());
	char *homedir = pw->pw_dir;
	strcat(homedir, "/.themes");
	userdirlength = dir_length(homedir);

	systemdirlength = dir_length("/usr/share/themes");

	gchar userfolderarray[userdirlength][100];
	gchar userthemenamearray[userdirlength][100];
	gchar systemfolderarray[systemdirlength][100];
	gchar systemthemenamearray[systemdirlength][100];

	// get the user folder valid themes and add to the size of validthemes
	walk_directories(homedir, "", userfolderarray, userthemenamearray);
	for (n = 0; n < userdirlength; n++)
	{
		if (strcmp(userfolderarray[n], "Empty")!= 0){
			validthemes++;
		}
	}
	// get the system folder valid themes and add to the size of validthemes
	walk_directories("/usr/share/themes", "", systemfolderarray, systemthemenamearray);
	for (n = 0; n < systemdirlength; n++)
	{
		if (strcmp(systemfolderarray[n], "Empty")!= 0){
			validthemes++;
		}
	}
	printf("Number of Valid index.themes is %i\n",validthemes);
	// make two arrays with the length of the total number of themes to populate later
	//gchar themes_id[validthemes][100];
	//gchar themes_name[validthemes][100];
	for (n = 0;  n < validthemes;  n++)
		//printf("%i\n",n);
		themes_id[n] = malloc (100);
		themes_name[n] = malloc (100);

	validthemes = 0;
	for (n = 0; n < userdirlength; n++)
	{
		if (strcmp(userfolderarray[n], "Empty")!= 0){
			printf("%s\n",userfolderarray[n]);
			//line below works fine
			strcpy(themes_id[validthemes], "What the hell is wrong with this!");
			printf("%s\n",themes_id[validthemes]);
			//line below causes segfault
			strcpy(themes_id[validthemes], userfolderarray[n]);
			strcpy(themes_name[validthemes], userthemenamearray[n]);
			validthemes++;
		}
	}
	for (n = 0; n < systemdirlength; n++)
	{
		if (strcmp(systemfolderarray[n], "Empty")!= 0){
			printf("%s\n",systemfolderarray[n]);
			strcpy(themes_id[validthemes], systemfolderarray[n]);
			strcpy(themes_name[validthemes], systemthemenamearray[n]);
			validthemes++;
		}
	}
	for (n = 0; n < validthemes; n++)
	{
		printf("%s Folder with theme name %s\n",themes_id[n], themes_name[n]);
	}
}

void main()
{
	populate_themes();
}
```

---

### Post by trent.josephsen on 2013-01-23
Have you tried printing out userfolderarray[n] to see what it contains before calling strcpy()? The simplest explanation is that it's not properly terminated, either because its length is greater than 100 or because it was never actually initialized. I could see either one happening. You should use strncpy() to avoid this kind of bug.

main() returns int, BTW.

Also, I'm just nitpicking, but your code-to-whitespace ratio seems a bit high to me.

---

### Post by Hairy_Palms on 2013-01-23
got it working now, this is the working code, i couldnt modify the string in place.

```
#include <sys/types.h>
#include <dirent.h>
#include <regex.h>
#include <stdio.h>
#include <gtk/gtk.h>
#include <string.h>
#include <unistd.h>
#include <pwd.h>
#include <stdlib.h>
 
enum {
    WALK_OK = 0,
    WALK_BADPATTERN,
    WALK_BADOPEN,
};

static gchar *themes_id[100];
static gchar *themes_name[100];

int walk_directories(const char *dir, const char *pattern, gchar theme_folders[][100], gchar theme_names[][100])
{
    struct dirent *entry;
    regex_t reg;
    DIR *d; 
    int i = 0;
    char *tempdname;
    FILE *file;

    gchar *subdir = NULL;
    GKeyFile *theme_file = NULL;
    GError *error = NULL;

    theme_file = g_key_file_new ();

    if (regcomp(&reg, pattern, REG_EXTENDED | REG_NOSUB))
        return WALK_BADPATTERN;
    if (!(d = opendir(dir)))
        return WALK_BADOPEN;
    while (entry = readdir(d))
	{
        if (!regexec(&reg, entry->d_name, 0, NULL, 0) )
		tempdname = entry->d_name;
		if( entry->d_type == DT_DIR && strcmp(entry->d_name,".") != 0 && strcmp(entry->d_name,"..") != 0)
			{
				subdir = g_build_filename(dir, tempdname, "/index.theme", NULL);
				//printf("%i %s %s\n",i,subdir,(g_key_file_load_from_file (theme_file, subdir, G_KEY_FILE_NONE, &error))?"true":"false");
				if (g_key_file_load_from_file (theme_file, subdir, G_KEY_FILE_NONE, &error)){
					//g_print("%s\n",g_key_file_get_string (theme_file, "X-GNOME-Metatheme", "Name", NULL));
					if (g_key_file_get_string (theme_file, "X-GNOME-Metatheme", "Name", NULL) != NULL){
						g_strlcpy(theme_names[i], g_key_file_get_string (theme_file, "X-GNOME-Metatheme", "Name", NULL), 100);
						strcpy(theme_folders[i], (tempdname));
						i++;
					}
					else if (g_key_file_get_string (theme_file, "Desktop Entry", "Name", NULL) != NULL){
						g_strlcpy(theme_names[i], g_key_file_get_string (theme_file, "Desktop Entry", "Name", NULL), 100);
						strcpy(theme_folders[i], (tempdname));
						i++;
					}
				}
				else{
					g_strlcpy(theme_names[i], "Empty", 100);
					strcpy(theme_folders[i], "Empty");
					i++;
				}			
				g_free (subdir);
				error = NULL;
			}
	}
    g_key_file_free (theme_file);
    closedir(d);
    regfree(&reg);
    return WALK_OK;
}

int dir_length(char *aDir)
{
	DIR *dp;
	int i = 0;
	struct dirent *ep;
	dp = opendir (aDir);

	if (dp != NULL)
	{
		while (ep = readdir (dp))
			i++;
		(void) closedir (dp);
	}
	i--;
	i--;
	return i;
}

int populate_themes()
{
	char * f;
	char * g;
	int n = 0;
	int systemdirlength = 0;
	int validthemes = 0;
	int userdirlength = 0;

	struct passwd *pw = getpwuid(getuid());
	char *homedir = pw->pw_dir;
	strcat(homedir, "/.themes");
	userdirlength = dir_length(homedir);

	systemdirlength = dir_length("/usr/share/themes");

	gchar userfolderarray[userdirlength][100];
	gchar userthemenamearray[userdirlength][100];
	gchar systemfolderarray[systemdirlength][100];
	gchar systemthemenamearray[systemdirlength][100];

	// get the user folder valid themes and add to the size of validthemes
	walk_directories(homedir, "", userfolderarray, userthemenamearray);
	for (n = 0; n < userdirlength; n++)
	{
		if (strcmp(userfolderarray[n], "Empty")!= 0){
			validthemes++;
		}
	}
	// get the system folder valid themes and add to the size of validthemes
	walk_directories("/usr/share/themes", "", systemfolderarray, systemthemenamearray);
	for (n = 0; n < systemdirlength; n++)
	{
		if (strcmp(systemfolderarray[n], "Empty")!= 0){
			validthemes++;
		}
	}
	printf("Number of Valid index.themes is %i\n",validthemes);
	// make two arrays with the length of the total number of themes to populate later
	//gchar themes_id[validthemes][100];
	//gchar themes_name[validthemes][100];
	for (n = 0;  n < validthemes;  n++)
		//printf("%i\n",n);
		themes_id[n] = malloc (100);
		themes_name[n] = malloc (100);

	validthemes = 0;
	for (n = 0; n < userdirlength; n++)
	{
		if (strcmp(userfolderarray[n], "Empty")!= 0){
			f = strdup(themes_id[validthemes]);
			strcpy(f, userfolderarray[n]);
			themes_id[validthemes] = f;

			g = g_strdup(themes_id[validthemes]);
			g_strlcpy(g, userthemenamearray[n], 100);
			themes_name[validthemes] = g;
			validthemes++;
		}
	}
	for (n = 0; n < systemdirlength; n++)
	{
		if (strcmp(systemfolderarray[n], "Empty")!= 0){
			f = strdup(themes_id[validthemes]);
			strcpy(f, systemfolderarray[n]);
			themes_id[validthemes] = f;

			g = g_strdup(themes_id[validthemes]);
			g_strlcpy(g, systemthemenamearray[n], 100);
			themes_name[validthemes] = g;
			validthemes++;
		}
	}
	/*for (n = 0; n < validthemes; n++)
	{
		printf("%s Folder with theme name %s\n",themes_id[n], themes_name[n]);
	}*/
	return validthemes;
}

void main()
{
	int n;
	int validthemes = populate_themes();
	for (n = 0; n < validthemes; n++)
	{
		printf("%s Folder with theme name %s\n",themes_id[n], themes_name[n]);
	}
}
```

as for the whitespace ratio, im used to python, just a habit :)
thanks for helping.

---

### Post by spjackson on 2013-01-23
+1 what trent.josephsen said.

Without compiling your code, the thing that stands out to me is this. If the themes directory contains a plain file (not a directory), then it will be included in dir_length but you won't write an entry in the array in walk_directories. Therefore your for loop would process more elements than have been initialised.

I don't know if that's your problem though.

---

### Post by Tony Flury on 2013-01-23
> **Hairy_Palms said:**
> got it working now, this is the working code, i couldnt modify the string in place.

```

... code snipped

```

as for the whitespace ratio, im used to python, just a habit :)
thanks for helping.

I don't think they are refering to your indentation, which actually is a good habit. They are refering to your lack of spacing in your code lines themselves and the lack of blank lines, which makes it very difficult to read as the eye cannot easily separate out the various parts of the construct. 

Nothing about python suggests not putting spaces within the text of your code.

---

### Post by Hairy_Palms on 2013-01-23
ah fair enough, i thought they were referring to the big indentations

---

### Post by Bachstelze on 2013-01-23
> **Hairy_Palms said:**
> ah fair enough, i thought they were referring to the big indentations

Big intendation is not a problem, but inconsistent indentation is. ;) 4 or 8 spaces, make up your mind.

Also, I haven't looked at your code but one thing that should be said is: just because it seems to work fine does not mean it's okay. Not all invalid memory accesses cause a segfault, so at the very least run your program in Valgrind to check for them.

---

### Post by Hairy_Palms on 2013-01-23
as far as my limited understanding the only memleaks will be the malloced arrays? (100 bytes each)
not best practice not to free them i understand, but the function is only going to run once in the larger program.

---

### Post by trent.josephsen on 2013-01-23
Just noticed this. How many times does the second malloc() get called?
```
	for (n = 0;  n < validthemes;  n++)
		//printf("%i\n",n);
		themes_id[n] = malloc (100);
		themes_name[n] = malloc (100);
```

One good example of how code working doesn't mean it's correct.

Again, you'll be well advised to stick with the strn* functions, which limit the number of bytes they write to avoid buffer overflows. Your code is not characteristic of the level of caution one should normally use when writing C.

For that matter, if you are using strdup(), you probably don't need the malloc() at all, since strdup() internally uses malloc() to obtain memory -- I say "probably" because I'm not too clear on what exactly you're trying to achieve, nor am I familiar enough with Gtk to say whether what you're doing is a good way to achieve it.

---

### Post by Hairy_Palms on 2013-01-23
> **trent.josephsen said:**
> Just noticed this. How many times does the second malloc() get called?
```
	for (n = 0;  n < validthemes;  n++)
		//printf("%i\n",n);
		themes_id[n] = malloc (100);
		themes_name[n] = malloc (100);
```

One good example of how code working doesn't mean it's correct.
oh god, missing braces, awesome >.< means i probably didnt need to do all the playing around with char pointers and strdup in the other loops to get it working.

well, the functions are meant to search all folders in /usr/share/themes and ~/.themes folder and see if they contain a file called index.theme, and then populate an array with the foldernames that do contain that file, and use the values from these files to populate another array, which i intend to use elsewhere later, but am just printing for now.

---

### Post by fct on 2013-01-24
A coding practice we use as work is this:

ALWAYS type the braces for conditionals and loops, even if there is only one line. Cause later more lines could be added, and forgetting the braces is easy.

So never forget the braces:
```

if (.....){
    // single line
} then {
    // single line
} else {
    // single line
}

for (....){
    // single line
}

```

---

### Post by Bachstelze on 2013-01-24
> **fct said:**
> A coding practice we use as work is this:

ALWAYS type the braces for conditionals and loops, even if there is only one line. Cause later more lines could be added, and forgetting the braces is easy.

So never forget the braces:
```

if (.....){
    // single line
} then {
    // single line
} else {
    // single line
}

for (....){
    // single line
}

```

"then" ? ;)

---

### Post by Hairy_Palms on 2013-01-24
you were right again, strdup meant i could drop the malloc loop completely

```

#include <sys/types.h>
#include <dirent.h>
#include <regex.h>
#include <stdio.h>
#include <gtk/gtk.h>
#include <string.h>
#include <unistd.h>
#include <pwd.h>
#include <stdlib.h>
 
enum {
	WALK_OK = 0,
	WALK_BADPATTERN,
	WALK_BADOPEN,
};

static gchar *themes_id[100];
static gchar *themes_name[100];

int walk_directories(const char *dir, const char *pattern, gchar theme_folders[][100], gchar theme_names[][100])
{
struct dirent *entry;
	regex_t reg;
	DIR *d; 
	int i = 0;
	char *tempdname;
	FILE *file;

	gchar *subdir = NULL;
	GKeyFile *theme_file = NULL;
	GError *error = NULL;

	theme_file = g_key_file_new ();

	if (regcomp(&reg, pattern, REG_EXTENDED | REG_NOSUB))
		return WALK_BADPATTERN;
	if (!(d = opendir(dir)))
		return WALK_BADOPEN;
	while (entry = readdir(d))
	{
	if (!regexec(&reg, entry->d_name, 0, NULL, 0) )
		tempdname = entry->d_name;
		if( entry->d_type == DT_DIR && strcmp(entry->d_name,".") != 0 && strcmp(entry->d_name,"..") != 0)
			{
				subdir = g_build_filename(dir, tempdname, "/index.theme", NULL);

				if (g_key_file_load_from_file (theme_file, subdir, G_KEY_FILE_NONE, &error)){
					//try and load the index.theme, if valid get the theme name
					if (g_key_file_get_string (theme_file, "X-GNOME-Metatheme", "Name", NULL) != NULL){
						g_strlcpy(theme_names[i], g_key_file_get_string (theme_file, "X-GNOME-Metatheme", "Name", NULL), 100);
						strcpy(theme_folders[i], (tempdname));
						i++;
					}
					//Shouldnt be needed by a lot of themes ignore the standard on this
					else if (g_key_file_get_string (theme_file, "Desktop Entry", "Name", NULL) != NULL){
						g_strlcpy(theme_names[i], g_key_file_get_string (theme_file, "Desktop Entry", "Name", NULL), 100);
						strcpy(theme_folders[i], (tempdname));
						i++;
					}
				}
				else{
					g_strlcpy(theme_names[i], "Empty", 100);
					strcpy(theme_folders[i], "Empty");
					i++;
				}			
				g_free (subdir);
				error = NULL;
			}
	}
	g_key_file_free (theme_file);
	closedir(d);
	regfree(&reg);
	return WALK_OK;
}

int dir_length(char *aDir)
{
	DIR *dp;
	int i = 0;
	struct dirent *ep;
	dp = opendir (aDir);

	if (dp != NULL)
	{
		while (ep = readdir (dp))
			i++;
		(void) closedir (dp);
	}
	i--;
	i--;
	return i;
}

int populate_themes()
{
	int n = 0;
	int systemdirlength = 0;
	int validthemes = 0;
	int userdirlength = 0;

	struct passwd *pw = getpwuid(getuid());
	char *homedir = pw->pw_dir;
	strcat(homedir, "/.themes");
	userdirlength = dir_length(homedir);

	systemdirlength = dir_length("/usr/share/themes");

	gchar userfolderarray[userdirlength][100];
	gchar userthemenamearray[userdirlength][100];
	gchar systemfolderarray[systemdirlength][100];
	gchar systemthemenamearray[systemdirlength][100];

	// increase the count of validthemes by the number in the users /.themes
	walk_directories(homedir, "", userfolderarray, userthemenamearray);
	for (n = 0; n < userdirlength; n++)
	{
		if (strcmp(userfolderarray[n], "Empty")!= 0){
			validthemes++;
		}
	}
	// increase the count of validthemes by the number in /usr/share/themes
	walk_directories("/usr/share/themes", "", systemfolderarray, systemthemenamearray);
	for (n = 0; n < systemdirlength; n++)
	{
		if (strcmp(systemfolderarray[n], "Empty")!= 0){
			validthemes++;
		}
	}

	validthemes = 0;
	for (n = 0; n < userdirlength; n++)
	{
		if (strcmp(userfolderarray[n], "Empty")!= 0){
			themes_id[validthemes] = g_strdup(userfolderarray[n]);

			themes_name[validthemes] = g_strdup(userthemenamearray[n]);

			validthemes++;
		}
	}
	for (n = 0; n < systemdirlength; n++)
	{
		if (strcmp(systemfolderarray[n], "Empty")!= 0){
			themes_id[validthemes] = g_strdup(systemfolderarray[n]);

			themes_name[validthemes] = g_strdup(systemthemenamearray[n]);

			validthemes++;
		}
	}
	return validthemes;
}

void main()
{
	int n;
	int validthemes = populate_themes();
	for (n = 0; n < validthemes; n++)
	{
		printf("%s Folder with theme name %s\n",themes_id[n], themes_name[n]);
	}
}

```

---

### Post by dwhitney67 on 2013-01-24
Yep, this looks like a safe operation:
```

...
	char *homedir = pw->pw_dir;
	strcat(homedir, "/.themes");
...

```

---

### Post by Bachstelze on 2013-01-24
> **dwhitney67 said:**
> Yep, this looks like a safe operation:
```

...
	char *homedir = pw->pw_dir;
	strcat(homedir, "/.themes");
...

```

Of course, what could go wrong? I can do the same thing in Python, look:

```
>>> import os
>>> homedir = os.getenv("HOME")
>>> homedir + "/.themes"
'/home/firas/.themes'

```

So surely it works the same in C, because Python is written in C, right?

---

### Post by fct on 2013-01-25
> **Bachstelze said:**
> "then" ? ;)

Damn, wrote that under need of caffeine. :lolflag:

---

### Post by Hairy_Palms on 2013-01-25
> **dwhitney67 said:**
> 
Yep, this looks like a safe operation:
	> char *homedir = pw->pw_dir;
	strcat(homedir, "/.themes");

> **Bachstelze said:**
> Of course, what could go wrong? I can do the same thing in Python, look:

```
>>> import os
>>> homedir = os.getenv("HOME")
>>> homedir + "/.themes"
'/home/firas/.themes'

```

So surely it works the same in C, because Python is written in C, right?

I take it thats a bad way to combine strings in C? why is that? i dont have much understanding of C's intricacies so id be glad for tips.

---

### Post by Bachstelze on 2013-01-25
The string pw->pw_dir is most probably stored in a memory area to which you cannot write. Thus when you try to append some data after it, you wil get a segfault (or at the very least, an unnoticed invalid memory access that will bite you in the **** later). What you should do is first copy pw->pw_dir to a memory area to which you may write, and append the data there. Something like:

```
char buf[100];
/*
 * Ensures that buf will always be null-terminated, even if
 * pw->pw_dir has 99 characters or more.  Aternatively, use
 * strlcpy() if available on your platform.
 */
buf[99] = 0;

strncpy(buf, pw->pw_dir, 99);
strncat(buf, "/.themes", 99-strlen(buf));
```

---

