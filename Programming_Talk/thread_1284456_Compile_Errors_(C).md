---
title: "Compile Errors (C)"
date: 2009-10-06
forum: Programming Talk
---

### Post by Jekshadow on 2009-10-06
I am writing a bot to harvest emails (just as an experiment, not to be used for spam), and I keep getting this error. It does not do anything yet, and I am just wondering why it is giving this error. I would like to debug it as I go so I don't have to deal with a ton of bugs at the end. Consider it released under the GPL. So just give me credit (Colin Warren).

```
bot.c:8: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘die’
bot.c:13: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘findEmails’
bot.c:28: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘findUrls’

```

the code is :

```
#include <stdio.h>

#include <stdlib.h>

int main() {
return 0;
}



bool die (char* reason, double errCode) {

	printf("ERR %d: %s\nKilling Program...", errCode, reason);

	return 1;

}



bool findEmails (char* fname) {

	char* email;

	FILE *tmpPage;

		if (!(tmpPage = fopen(TMP_DIR+fname, "r"))) 

			return die("FAILED TO OPEN PAGE TO PARSE!", 1);

	while (fscanf(tmpPage, "<a href=\"mailto:%s\"", email) != EOF) {

		FILE *emailList;

		emailList = fopen ("cfg/emails.lst", "a");

		fprintf(emailList, email+"\n");

		fclose(emailList);

	}

	fclose (tmpPage);

	remove("/tmp/spyder/"+fname);

}



bool findUrls (char* fname) {

	char* url;

	FILE *tmpPage;

	if (!(tmpPage = fopen(TMP_DIR+fname, "r")))

		return die("FAILED TO OPEN PAGE TO PARSE!", 1);

	while (fscanf(tmpPage, "<a href=\"%s\"", url) != EOF) {

		if (!isEmail(url)) {

			FILE *urlList;

			urlList = fopen ("cfg/url.lst", "a");

			fprintf(urlList, url+"\n");

			fclose(urlList);

		}

	}

}



```

---

### Post by dribeas on 2009-10-06
You have quite some mistakes, the first one is (the one you are asking about) that 'bool' is not a type in C (it is in C++), so if you intend to compile with a C compiler you should use 'int' as the type (where 0 is false, !=0 true).

There are many more, such as strings in C (char*'s) not being appendable with the + operator, TMP_DIR not being defined anywhere. Anyway this should get you in the way.

---

### Post by dwhitney67 on 2009-10-06
The OP could include <stdbool.h> if 'bool' is what is really wanted.

P.S.  If the OP wants to return a boolean from the functions, ummm, I would suggest he do it.  From the code that was posted, nothing is being returned (except in die()).

---

