---
title: "C - Replacing a string in a string"
date: 2009-11-01
forum: Programming Talk
---

### Post by wolterh on 2009-11-01
I've been trying to develop my own function to replace strings (strings in strings, not just single characters) but I've failed every time. I've come here to see if anyone can help me in this:

```

#include <stdio.h>
#include <glib.h>
#include <string.h>

/* In this attempt I tried to use GRegex, but I don't quite understand the api */
void string_replace (gchar* original,
  const gchar* portion,
  const gchar* replacement) {
	GError* error;
	error = NULL;
	GRegex* regex = g_regex_new ("hello", G_REGEX_CASELESS, 0, &error);
	gchar* temp_string;
	temp_string = g_regex_replace_literal (regex, "ello", 5, 0, "ola", 0, &error);
	printf ("%s\n", temp_string);
	original = strdup(temp_string);
	g_free (temp_string);
}

/* This one is a more manual attempt */
void string_replace2 (char* original, const char* piece, const char* replacement) {
	int iter1;
	int iter2;
	int replace = 1; // FALSE
	int firstmatch = -1;
	int orig_len = strlen (original);
	int piec_len = strlen (piece);
	for (iter1 = 0; iter1 < orig_len; iter1++) {
		for (iter2 = 0; iter2 < piec_len; iter2++) {
			if (original[iter1] == piece[iter2]) {
				firstmatch = (firstmatch == -1) ? iter1 : firstmatch;
				printf ("%c : %c\n", original[iter1], piece[iter2]);
			}
			else {
				//replace = 0;
			}
		}
	}
	if (replace == 1) {
		// This starts replacing always at the begining of the function
		//(firstmatch is always 0 I don't know why
		printf ("%d\n", firstmatch);
		int limit = strlen (replacement);
		for (iter1 = 0; iter1 < limit; iter1++) {
			original[firstmatch+iter1] = replacement[iter1];
		}
		/* This works:
		original[1] = replacement[0];
		original[2] = replacement[1];
		original[3] = replacement[2];
		*/
	}
}

int main(int argc, char** argv)
{
	char* hello = strdup("hola muchachos");
	string_replace2 (hello, "chos", "chas");
	printf ("%s\n", hello);
        // The above returns "chas muchachos", and not "hola muchachas"
	return 0;
}

```

I've done other tries, but their are all pretty similar to the string_replace2 function.

---

### Post by dwhitney67 on 2009-11-01
Wow, that's a lot of code.

I would've done it this way:
```

#include <string.h>
#include <stdlib.h>
#include <stdio.h>

char* replace(const char* orig_str, const char* old_token, const char* new_token)
{
   char*       new_str = 0;
   const char* pos = strstr(orig_str, old_token);

   if (pos)
   {
      new_str = calloc(1, strlen(orig_str) - strlen(old_token) + strlen(new_token) + 1);

      strncpy(new_str, orig_str, pos - orig_str);
      strcat(new_str, new_token);
      strcat(new_str, pos + strlen(old_token));
   }

   return new_str;
}

int main()
{
   const char* orig_str = "Hola Muchachos!";
   char*       new_str  = replace(orig_str, "chos", "chas");

   printf("orig_str = %s\n", orig_str);

   if (new_str) {
      printf("new_str  = %s\n", new_str);

      free(new_str);
   }
   else {
      printf("No match for conversion!\n");
   }

   return 0;
}

```

---

### Post by wolterh on 2009-11-01
Didn't I say that it was not valid to use magic in this function?
That piece of code works perfectly!! Nobody ever before could give me something so small and functional! I'll study your code profoundly.

Thanks a lot!

---

### Post by dwhitney67 on 2009-11-01
> **woli said:**
> Didn't I say that it was not valid to use magic in this function?
That piece of code works perfectly!! Nobody ever before could give me something so small and functional! I'll study your code profoundly.

Thanks a lot!

Here's an alternative in case your intent was to modify the original string (and not produce a copy as I did earlier).
```

#include <string.h>
#include <stdlib.h>
#include <stdio.h>

void replace(char** str, const char* old_token, const char* new_token)
{
   char* pos = strstr(*str, old_token);

   if (pos)
   {
      char* tmp = calloc(1, strlen(*str) - strlen(old_token) + strlen(new_token) + 1);

      strncpy(tmp, *str, pos - *str);
      strcat(tmp + (pos - *str), new_token);
      strcat(tmp, pos + strlen(old_token));

      free(*str);
      *str = calloc(1, strlen(tmp) + 1);

      strcpy(*str, tmp);

      free(tmp);
   }
}

int main()
{
   char* str = strdup("Hola Muchachos!");

   replace(&str, "Hola", "Que tal");

   printf("str = %s\n", str);

   free(str);

   return 0;
}

```

---

### Post by wolterh on 2009-11-02
Thanks for the alternative! It will certainly get me understanding better these functions (once I finish studying for this exam week though)

---

