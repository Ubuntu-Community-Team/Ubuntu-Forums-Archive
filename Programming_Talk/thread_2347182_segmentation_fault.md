---
title: "segmentation fault"
date: 2016-12-22
forum: Programming Talk
---

### Post by garamaleki on 2016-12-22
Hello guys , i'm new to c and i'm trying to read a page using curl but i'm getting SIGSEGV error
here is my code :
```

#include <stdio.h>
#include <ctype.h>
#include <stdlib.h>
#include <curl/curl.h>
#include <string.h>


size_t static curl_write(void *buffer, size_t size , size_t nmemb,void *userp){
    userp += strlen((const char *) userp);
    memcpy(userp,buffer,nmemb);
    return nmemb;
}




int max(int numberOne , int numberTwo){
	if(numberOne > numberTwo)
		return numberOne;
	return numberTwo;
}




void findMostFrequent(char str[],long strlength,char result[]){


	long i,j ;// counters
	int wordCounter = 0;
	int charCounter = 0;
	char words[10000][75];


	for(i = 0; i < 100000 - 6 ; i++){


		 if(str[i] != ' ' && (str[i+1] == ' ' || str[i+1] == '\t' || str[i+1] =='\r' || str[i+1] == '\n')){
			charCounter = 0;
			wordCounter++;
		}
		else if((str[i] == ' ' || str[i] == '\t' || str[i] =='\r' || str[i] == '\n') && isalpha(str[i+1]) != 0 ){
			charCounter = 0;
			continue;
		}
		else{
			words[wordCounter][charCounter] = str[i];
			charCounter++;
		}
	}




//	for(i = 0;i<=wordCounter;i++){
//		printf("%s : %d\n",words[i],strlen(words[i]));
//	}




//	printf("%d\n",wordCounter+1);
//	printf("i is %d\n",i);
	int timesOfOccurance[wordCounter+1];


	for(i = 0; i <= wordCounter;i++){
		timesOfOccurance[i] = 1;
	}


	for(i = 0; i < wordCounter; i++){
		for(j = i + 1; j <= wordCounter; j++){
			if(strcmp(words[i],words[j]) == 0){
				timesOfOccurance[i]++;
			}
		}
	}


	int MAX = 0;


	for(i = 0; i <=wordCounter; i++){
		MAX = max(MAX,timesOfOccurance[i]);
	}


	char res[100];
	int halat = 0;
	for(i = 0; i<= wordCounter;i++){
		if(timesOfOccurance[i] == MAX){
			if(halat == 0){
				strcpy(res,words[i]);
				halat = 1;
			}
			if(strcasecmp(res,words[i]) > 0){
				strcpy(res,words[i]);
			}
		}
	}
	//strcpy(result,res);


	printf("%d MAX\n",MAX);
//	for(i = 0; i<= wordCounter;i++)
//		printf("%s : %d\n",words[i],timesOfOccurance[i])	;
}




int main(){
    CURL *curl;
    CURLcode res;
    char *s = (char *)malloc(100000);


    curl = curl_easy_init();
    if(curl){
        curl_easy_setopt(curl,CURLOPT_URL,"http://team30:xxxxxxxxxxx@www.fop-project.ir/phase0");
		curl_easy_setopt(curl,CURLOPT_WRITEFUNCTION,curl_write);
        curl_easy_setopt(curl,CURLOPT_WRITEDATA,s);
        res = curl_easy_perform(curl);
       // printf("%s",s);
        curl_easy_cleanup(curl);
    }


    FILE *in = fopen("sample.txt","w");
    fprintf(in,"%s",s);
    fclose(in);






    char str[100000];
    FILE *file = fopen("sample.txt","rb");
    int i;
    for(i = 0;i<100000;i++){


        str[i] = fgetc(file);
    }
	puts(str);






    fclose(file);








   char result[100];


  findMostFrequent(str,strlen(str),result);
    printf("%s",result);




}


```

I've searched about rhis error and found some articles , but i can't fix this ....

---

### Post by Odexios on 2016-12-22
There is a clear text username with password in there, I suggest you to remove them

EDIT: And change the password, if at all possible.

---

### Post by kpatz on 2016-12-22
Is this a homework assignment?  In case it is, I'll give a little guidance but it's up to you to figure out the answer.

A segmentation fault occurs when your program accesses memory that doesn't belong to it.  Most commonly this is due to exceeding the size of an array.

Another possible cause is not terminating a string with a null character.

There's places in the code where you have a size hard coded (i.e. 100000).  What if the file being downloaded is larger?  Smaller?

What if there's more than 10000 "words"? 

See if these hints help.

---

