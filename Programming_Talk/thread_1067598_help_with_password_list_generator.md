---
title: "help with password list generator"
date: 2009-02-12
forum: Programming Talk
---

### Post by c@sp3r on 2009-02-12
I'm trying to do a password list. I wan to be able to save in a file all possibles combination up to a determine length. The list should start with 0,1,3.....a,b,c.....0a,0b,0c, etc. all I have been able to do is do the list with only all possible combinations for the determine length only example if length is 3 the list starts with 001,002,003.... instead of 0,1,2.....001,002,003,etc. Can somebody help with this I'm stuck and out of ideas. Thanks a lot!!! 
This my code so far
```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

void printAllPossiblePasswords(int length, const char* charset){
    char* str;
    const char** counters;
    int i;
    FILE *password;

	password=fopen("passwords.txt", "w+");
    str = malloc(length+1);
    counters = malloc(sizeof(char*)*(length + 1));
    counters[length] = 0;
    str[length] = 0;
    for (i = 0; i < length; i++)
    {
        counters[i] = charset;
    }

    while(1)
    {
        for (i = 0; i < length; i++)
	    str[i] = *(counters[i]);

        fprintf(password,"%s\n", str);

        counters[0]++;
        for (i = 0; (i < length) && (*(counters[i]) == 0); i++)
        {
            counters[i] = charset;
            counters[i+1]++;
        }

        if (i == length)
	    break;
    }

    free(str);
    free(counters);
    fclose(password);
}

int main ()
{

    int length;

    system("clear");
    printf("****************Password Hash Generator****************\n");
	printf("Enter the length of the password:");
	scanf("%d",&length);
	printf("Generating list...\n\n");
    printAllPossiblePasswords(length, "1234567890qwertyuiopasdfghjklzxcvbnmQWERTYUIOPASDFGHJKLZXCVBNM[]-=;'\\,./!@#$%^&*()_+{}:\"|<>?~`");
    //printAllPossiblePasswords(length, "1234567890qwertyuiopasdfghjklzxcvbnm");

    FILE *hash;
    hash = popen("openssl passwd -salt -crypt -in \"passwords.txt\" > \"hashes.txt\"", "r");
    pclose(hash);

    printf("With great powers  come great responsabilities!");

    return 1;
}

```

---

### Post by drewbenn on 2009-02-12
Change

```
    printAllPossiblePasswords(length, "1234567890qwertyuiopasdfghjklzxcvbnmQWERTYUIOPASDFGHJKLZXCVBNM[]-=;'\\,./!@#$%^&*()_+{}:\"|<>?~`");

```


to


```

    for (int n = 1; n <= length; n++) {
       printAllPossiblePasswords(n, "1234567890qwertyuiopasdfghjklzxcvbnmQWERTYUIOPASDFGHJKLZXCVBNM[]-=;'\\,./!@#$%^&*()_+{}:\"|<>?~`");
    }

```

:guitar:

---

