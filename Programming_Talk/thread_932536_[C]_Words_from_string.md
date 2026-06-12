---
title: "[C] Words from string"
date: 2008-09-28
forum: Programming Talk
---

### Post by carrie.peary on 2008-09-28
Basically I want to separate out words from a string, and store those in another array. Basically taking "I like money" to "I" "like" "money". Spaces would be the only deliminter. But I seem to have run into a problem of building a word string to store one character at a time until a space if found. Here is what I have so far:

```

int main(void)
{
	char str[64];
	char words[64];
	char *word = "";
	char *schar = "";
	int i = 0;
	int j = 0;
	
      //Get string
	printf("String-> ");
	fgets(str, 64, stdin);
	
	printf( "You entered string: %s\n", str );
	
       //Loop through string character by character
	while(str[i] != '\0')
	{
            //If a space, store word into words array, make 'word' string empty
	    if (str[i] == ' ') {
	    	words[j] = *word;
	    	j++;
	    	word = "";
	    }
            //
	    else {
	    	schar = str[i];
	    	word = strcat(word, schar);
	    }
	    i++;\
	}
 return 0;
}

```

---

### Post by nvteighen on 2008-09-28
You have a serious problem there. What's "words" supposed to be? An array of characters or an array of strings? If it's the second, don't you think you're using the wrong data type?

Also, you may have a look at standard functions strtok() and strtok_r() for parsing "words" in a string. If you haven't already, install the "manpages-dev" package and then, in a Terminal type "man strtok" for more information.

Is this related to your shell project, btw? (just curious... :p)

---

### Post by carrie.peary on 2008-09-28
> **nvteighen said:**
> You have a serious problem there. What's "words" supposed to be? An array of characters or an array of strings? If it's the second, don't you think you're using the wrong data type?

Also, you may have a look at standard functions strtok() and strtok_r() for parsing "words" in a string. If you haven't already, install the "manpages-dev" package and then, in a Terminal type "man strtok" for more information.

Is this related to your shell project, btw? (just curious... :p)

Yes to your last question, I never quite got strings in C in the first place, and it's been 2yrs since that class...so I'm still trying to pick it all back up.

Ok, i did a rewrite but now when I enter a string, words stored in 'words', when I print say words[0] all I get is the first character, even though I've allocated memory.

```

	char str[64];
	char **words;
	char *str2;
	int i = 0;
	char *newword;
	int l = 0;
	
	words = malloc(11 * sizeof(char));
	
	for(l=0; l<11; ++l )
	{
	    words[l] = malloc(11 * sizeof(char));  /* 10 characters + '\0' */
	}
	
	printf("mshell-> ");
	fgets(str, 64, stdin);
	
	printf( "You entered string: %s\n", str );
	
	str2 = str;
	newword = strtok(str2, " ");
	
	while(newword != 0)
	{	
		if (i != 10) {
			*words[i] = *newword;
	
			printf("Newword: %s", newword);
			
			/* Get the next word from the string                             */
			newword = strtok(0, " ");
			/* Increment i, since we are trying to add another word.        */
			++i;
		}
	}
	
	printf("Words: %s\n", words[0]);

```

---

