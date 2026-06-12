---
title: "Using PCRE in C to do string replacement"
date: 2008-11-23
forum: Programming Talk
---

### Post by bluedalmatian on 2008-11-23
I'm experimenting with PCRE. I can do simple matching to determine if a match was found or not but I can't get replacement to work and I cant find an example on the web of how to do it.

Am I right in thinking that PCRE can replace the matched part of the input with a new string by writing into an array the start & finish index of the match?

The following little program is supposed to replace the 61 with 63 but the result value keeps coming out as 2 (error). I suspect Im doing something wrong with that ovector array?

Thanks

#include <stdio.h>
#include <pcre.h>
#include <string.h>
int main()
{
	//look at the str  612780 and see if it starts with 61
	
	pcre *regexp;
	const char *error;
	int erroffset;
	char *pattern = "^61([0-9]+)$";
	char *string = "612000";
	char* replacement = "63";
	regexp = pcre_compile(pattern,0,&error,&erroffset,NULL);
	if (!regexp)
	{
		printf("Error compiling expression\n");
                exit(1);
 
	}
	int result;

	int ovectorlength = 30;
	int ovector[ovectorlength];
	result = pcre_exec(regexp,NULL,string,strlen(string),0,0,ovector,ovectorlength);


	//result = 0 means found, -1 not found, other value error
	printf("Result: %d\n",result);
	
	if (result == 0)
	{
		
		//match found, locate it and do replacement
          
                //??=which elements should i put in here
 
		int start = ovector[???]; //start of match
		int end = (ovector[????]);//end of match
		//...do replacement here
	}

	pcre_free(regexp);

return (0);
}

---

