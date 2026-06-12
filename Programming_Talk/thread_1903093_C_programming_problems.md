---
title: "C programming problems"
date: 2012-01-01
forum: Programming Talk
---

### Post by xtjacob on 2012-01-01
Hello, I'm trying to write a weather program for a school project. However I keep running into errors and I'm not sure what the problem with my program is.

```
//************************************************************
//              Copyright 2012
//               Jacob Boline
//************************************************************

#include <stdio.h>
#include <curl/curl.h>
#include <string.h>
#include <stdlib.h>

void main()
{
  char url[100] = "http://api.wunderground.com/api/59eb6f72cabe560e/"; /*Declares inital URL*/
  char location[5];
  char feature[12];
  char temp[7] = "temp_f";
  char tempf[5];
  int lnth;
  printf("Please enter your zip code:\n");                   /* Asks for location. */
  scanf("%s", location);	                             /* Stores location. */
  printf("Please enter what information you would like:\n"); /* Asks for information. */
  scanf("%s", feature);                                      /* Stores information. */
  lnth = strlen(feature);                                    /* Finds length of string. */
  strncat(url, feature, lnth);                               /* Appends feature to URL */
  strncat(url, "/q/", 3);
  strncat(url, location, 5);                                 /* Appends location to URL. */
  strncat(url, ".json", 5);
  curlf(url);                                                /* Calls cURL function. */
  printf("File downloaded.\n");
  tempf = Search_in_File(temp);
  printf("%s\n", tempf);
}

void curlf(const char* url, char *str)
{
  CURL *json;
  FILE *wdata;
  CURLcode res;
  json = curl_easy_init();                           /* Start downloading process. */
  curl_easy_setopt(json, CURLOPT_URL, url);          /* Tells cURL what the URL is. */
  wdata = fopen( "wdata.json", "w");                 /* Create file to save data. */
  curl_easy_setopt(json, CURLOPT_WRITEDATA, wdata);  /* Tells cURL to save sata to wdata. */
  curl_easy_perform(json);                           /* Performs download. */
  curl_easy_cleanup(json);                           /* Cleans up. */
  fclose(wdata);                                     /* Close file. */
}

char Search_in_File(char *str) {
  FILE *fp;
  char temp[512];
  char sep[] = ":,";
  char *result = NULL;

  fp = fopen("wdata.json", "r");

  while(fgets(temp, 512, fp) != NULL)
  {
    if((strstr(temp, str)) != NULL)
    {
      result = strtok( temp, sep );
      result = strtok( NULL, sep );
      return result;
    }
  }

 fclose(fp);
}
```
The program is supposed to download a file, parse it for temp_f in order to find the temperature, return it to the main function, and then print it. However I keep getting these errors when I attempt to compile it: ```
main.c: In function ‘main’:
main.c:30:9: error: incompatible types when assigning to type ‘char[5]’ from type ‘int’
main.c: At top level:
main.c:34:6: warning: conflicting types for ‘curlf’ [enabled by default]
main.c:28:3: note: previous implicit declaration of ‘curlf’ was here
main.c:48:6: error: conflicting types for ‘Search_in_File’
main.c:30:11: note: previous implicit declaration of ‘Search_in_File’ was here
main.c: In function ‘Search_in_File’:
main.c:62:7: warning: return makes integer from pointer without a cast [enabled by default]

```
I'm compiling with "gcc main.c -l curl -o main". Can anybody help me? :confused:

---

### Post by MadCow108 on 2012-01-01
there are a couple of issues in that code.

1. the signature of all functions must be known before their use
either place the whole functions at the top of the file or just their prototypes (= the first line with a ; at the end)
```
void curlf(const char* url, char *str);
int main()
{
curlf(bla);
}

void curlf(const char* url, char *str)
{
// do something
}

```

2. Search_in_File has a wrong return type, it must return char* and the variable receiving the result must be the same. you can't return arrays in C.

3. Search_in_File returns a pointer to stack storage which will be invalid when the function ends, you should strdup the result to place it on the heap, return the pointer to that and also make sure free it again later.

4. what happens when your target search string gets cut in half by the 512 buffered read?

5. there may be more issues I overlooked.

to parse json you should prefer using a library like e.g. json-c

---

### Post by Bachstelze on 2012-01-01
main returns int so

```
void main()
```

should be

```
int main(void)
```

Your other problems all come from the fact that you don't seem to be sure what exactly the types of your functions are. For example you say Search_in_File returns a char, but then you are making it return a char*. So make up your mind once and for all about what the types of your functions (return type and arguments) are, make a prototype for it at the top of your source file, and then *stick to it*.

---

### Post by xtjacob on 2012-01-01
> **MadCow108 said:**
> 
4. what happens when your target search string gets cut in half by the 512 buffered read?


What do you mean?

---

### Post by MadCow108 on 2012-01-01
say sour searching for "abcd" and that string is in position 510,
so the strstr will not find the string as "ab" will be in the result of the first fgets and "cd" will be in the next.


also the file is never closed when the search succeeds.

---

### Post by ofnuts on 2012-01-01
You'll get burned by:
 ```

  char temp[7] = "temp_f";   
...
strncat(url, "/q/", 3);   
...
strncat(url, ".json", 5); 

```
No need to specify a length for safety since this is your source code, not some string of dubious origin/content. And if you ever have to change the strings, you may forget to update the length and have all kind of weird buffer overflows.

---

### Post by xtjacob on 2012-01-01
> **ofnuts said:**
> You'll get burned by:
 ```

  char temp[7] = "temp_f";   
...
strncat(url, "/q/", 3);   
...
strncat(url, ".json", 5); 

```
No need to specify a length for safety since this is your source code, not some string of dubious origin/content. And if you ever have to change the strings, you may forget to update the length and have all kind of weird buffer overflows.

I tried getting rid of the lengths, but when I try to compile it gcc says "too few arguments".

---

### Post by xtjacob on 2012-01-01
Alright, now my code compiles perfectly:
```
//************************************************************
//              Copyright 2012
//               Jacob Boline
//************************************************************

#include <stdio.h>
#include <curl/curl.h>
#include <string.h>
#include <stdlib.h>

void curlf(const char* url);
char *Search_in_File(char *str);

int main(void)
{
  char url[100] = "http://api.wunderground.com/api/59eb6f72cabe560e/"; /*Declares inital URL*/
  char location[5];
  char feature[12];
  char temp[7] = "temp_f";
  char *tempf;
  int lnth;
  printf("Please enter your zip code:\n");                   /* Asks for location. */
  scanf("%s", location);	                             /* Stores location. */
  printf("Please enter what information you would like:\n"); /* Asks for information. */
  scanf("%s", feature);                                      /* Stores information. */
  lnth = strlen(feature);
  strncat(url, feature, lnth);                               /* Appends feature to URL */
  strncat(url, "/q/", 3);
  strncat(url, location, 5);                                 /* Appends location to URL. */
  strncat(url, ".json", 5);
  curlf(url);                                                /* Calls cURL function. */
  printf("File downloaded.\n");
  tempf = Search_in_File(temp);
  printf("%s\n", tempf);
}

void curlf(const char* url)
{
  CURL *json;
  FILE *wdata;
  CURLcode res;
  json = curl_easy_init();                           /* Start downloading process. */
  curl_easy_setopt(json, CURLOPT_URL, url);          /* Tells cURL what the URL is. */
  wdata = fopen( "wdata.json", "w");                 /* Create file to save data. */
  curl_easy_setopt(json, CURLOPT_WRITEDATA, wdata);  /* Tells cURL to save sata to wdata. */
  curl_easy_perform(json);                           /* Performs download. */
  curl_easy_cleanup(json);                           /* Cleans up. */
  fclose(wdata);                                     /* Close file. */
}

char *Search_in_File(char *str) {
  FILE *fp;
  char temp[512];
  char sep[] = ":,";
  char *result = NULL;

  fp = fopen("wdata.json", "r");

  while(fgets(temp, 512, fp) != NULL)
  {
    if((strstr(temp, str)) != NULL)
    {
      result = strtok( temp, sep );
      result = strtok( NULL, sep );
      fclose(fp);
      return result;
    }
  }
}
```

---

### Post by Bachstelze on 2012-01-01
You still have a problem: if the call to strstr in Search_in_File returns NULL every time, the function will return an undefined value.

---

### Post by xtjacob on 2012-01-01
> **Bachstelze said:**
> You still have a problem: if the call to strstr in Search_in_File returns NULL every time, the function will return an undefined value.

Alright, I'm going to try and switch it over to json-c for the parser instead.

---

### Post by ofnuts on 2012-01-02
> **xtjacob said:**
> I tried getting rid of the lengths, but when I try to compile it gcc says "too few arguments".use strcat() instead of strncat()

---

### Post by Petrolea on 2012-01-02
> **ofnuts said:**
> use strcat() instead of strncat()

Yes, strncat takes one more argument than strcat.

[http://www.cplusplus.com/reference/clibrary/cstring/strncat/](http://www.cplusplus.com/reference/clibrary/cstring/strncat/)
[http://www.cplusplus.com/reference/clibrary/cstring/strcat/](http://www.cplusplus.com/reference/clibrary/cstring/strcat/)

---

### Post by dwhitney67 on 2012-01-02
@ xtjacob

In the US, Zip Codes are composed of a minimum of 5 digits, but sometimes with the 4-digit extension (eg. 12345-9876).  If you plan to store this as a string within a char-array, make sure that you augment the array size to include space for the terminating null-character.
```

...
  **char location[5]**;   <-- SHOULD BE 11, NOT 5
...
  printf("Please enter your zip code:\n");                   /* Asks for location. */
  scanf("%s", location);
...

```

Also you should be aware that reading raw-input using scanf() or fscanf() is considered bad practice.  Rely on fgets() or getline().  The reason for avoiding scanf() is so that you can mitigate the possibility of incurring a buffer overrun.  Back to the example above, where you specified an array for storing the zip code; what would be the ramifications if the operator enters a string that is greater than the size of the buffer?  A little hint:  the variables following the declaration of 'location' will be trampled on with garbage data.

---

### Post by ofnuts on 2012-01-02
> **dwhitney67 said:**
> @ xtjacob

In the US, Zip Codes are composed of a minimum of 5 digits, but sometimes with the 4-digit extension (eg. 12345-9876).  If you plan to store this as a string within a char-array, make sure that you augment the array size to include space for the terminating null-character.
```

...
  **char location[5]**;   <-- SHOULD BE 11, NOT 5
...
  printf("Please enter your zip code:\n");                   /* Asks for location. */
  scanf("%s", location);
...

```Also you should be aware that reading raw-input using scanf() or fscanf() is considered bad practice.  Rely on fgets() or getline().  The reason for avoiding scanf() is so that you can mitigate the possibility of incurring a buffer overrun.  Back to the example above, where you specified an array for storing the zip code; what would be the ramifications if the operator enters a string that is greater than the size of the buffer?  A little hint:  the variables following the declaration of 'location' will be trampled on with garbage data.
You still have to parse the input with sscanf :) However, you can use the %Ns format specification (read at most N characters), or, if using Gnu extensions, "%as" (dynamically allocates whatever is needed to hold the string).

---

### Post by xtjacob on 2012-01-02
Here's what I have for the json parser, however I'm having trouble getting it to read the file.

```
#include <json/json.h>
#include <stdio.h>

void json_parse(json_object * jobj);

int main(void) {
  FILE *fp;
  fp = fopen("wdata.json", "r");
  json_object * jobj = json_tokener_parse(fp);
  json_parse(jobj);
}

void json_parse(json_object * jobj) {
 enum json_type type;
 json_object_object_foreach(jobj, key, val) {
 printf("value: %d\n", json_object_get_int(val));
 }
}

```

Compiler says:
```
jsonparser.c: In function ‘main’:
jsonparser.c:9:3: warning: passing argument 1 of ‘json_tokener_parse’ from incompatible pointer type [enabled by default]
/usr/include/json/json_tokener.h:90:28: note: expected ‘const char *’ but argument is of type ‘struct FILE *’

```

---

### Post by xtjacob on 2012-01-02
> **dwhitney67 said:**
> @ xtjacob

In the US, Zip Codes are composed of a minimum of 5 digits, but sometimes with the 4-digit extension (eg. 12345-9876).  If you plan to store this as a string within a char-array, make sure that you augment the array size to include space for the terminating null-character.
```

...
  **char location[5]**;   <-- SHOULD BE 11, NOT 5
...
  printf("Please enter your zip code:\n");                   /* Asks for location. */
  scanf("%s", location);
...

```

Also you should be aware that reading raw-input using scanf() or fscanf() is considered bad practice.  Rely on fgets() or getline().  The reason for avoiding scanf() is so that you can mitigate the possibility of incurring a buffer overrun.  Back to the example above, where you specified an array for storing the zip code; what would be the ramifications if the operator enters a string that is greater than the size of the buffer?  A little hint:  the variables following the declaration of 'location' will be trampled on with garbage data.

I didn't realize that about the zipcodes, thanks for that tip!

---

### Post by dwhitney67 on 2012-01-02
> **xtjacob said:**
> Here's what I have for the json parser, however I'm having trouble getting it to read the file.

```
#include <json/json.h>
#include <stdio.h>

void json_parse(json_object * jobj);

int main(void) {
  FILE *fp;
  fp = fopen("wdata.json", "r");
  json_object * jobj = json_tokener_parse(fp);
  json_parse(jobj);
}

void json_parse(json_object * jobj) {
 enum json_type type;
 json_object_object_foreach(jobj, key, val) {
 printf("value: %d\n", json_object_get_int(val));
 }
}

```

Compiler says:
```
jsonparser.c: In function ‘main’:
jsonparser.c:9:3: warning: passing argument 1 of ‘json_tokener_parse’ from incompatible pointer type [enabled by default]
/usr/include/json/json_tokener.h:90:28: note: expected ‘const char *’ but argument is of type ‘struct FILE *’

```

I don't know anything about the json parser tools, but it would seem that from the compiler error you are getting, that the json_tokener_parse() requires a const char*, perhaps the file name itself, not the file pointer.

---

### Post by xtjacob on 2012-01-02
> **dwhitney67 said:**
> I don't know anything about the json parser tools, but it would seem that from the compiler error you are getting, that the json_tokener_parse() requires a const char*, perhaps the file name itself, not the file pointer.

I just tried replacing it and it compiles, but when I run it it segfaults.

---

### Post by Barrucadu on 2012-01-02
I think json_tokener_parse takes the string to parse as json, in this case the content of the file.

---

### Post by xtjacob on 2012-01-02
I got the code off of [this]("http://joysofprogramming.com/json_object_get_int/") website and I'm trying to modify it. Here's what it was originally if that helps. ```
#include <json/json.h>
#include <stdio.h>
 
void json_parse(json_object * jobj) {
 enum json_type type;
 json_object_object_foreach(jobj, key, val) {
 type = json_object_get_type(val);
 switch (type) {
 case json_type_int: printf("type: json_type_int, ");
 printf("value: %d\n", json_object_get_int(val));
 break;
 }
 }
}
int main() {
 char * string = "{ \"colors\" : 7,\
 \"continents\" : 7,\
 \"oceans\" : 5\
 }";
 printf ("JSON string: %s\n", string);
 json_object * jobj = json_tokener_parse(string);
 json_parse(jobj);
}
```

---

### Post by Barrucadu on 2012-01-02
So, you just need to read the file into memory and pass it to json_tokener_parse.

---

### Post by xtjacob on 2012-01-02
> **Barrucadu said:**
> So, you just need to read the file into memory and pass it to json_tokener_parse.

Doesn't this read it into memory?
```
FILE *fp;
  fp = fopen("wdata.json", "r");
```
And this passes it to json_tokener_parse?
```
json_object * jobj = json_tokener_parse(fp);
```

---

### Post by Barrucadu on 2012-01-02
No, that just opens the file. You have to fread it into a char* first (or use something like mmap).

---

### Post by xtjacob on 2012-01-02
Sorry, but how do I do that?

---

### Post by Barrucadu on 2012-01-02
I haven't tested it, but something like this would probably work:

```

FILE* fp;
char* buffer;
long  fsize;

/* Open the file */
fp = fopen (FILENAME, "r");
if (fp == NULL) return 1;

/* Get the size of the file */
fseek (fp, 0, SEEK_END);
fsize = ftell (fp) + 1;
fseek (fp, 0, SEEK_SET);

/* Allocate the buffer */
buffer = calloc (fsize, sizeof (char));
if (buffer == NULL) return 1;

/* Read the file */
fread (buffer, sizeof (char), fsize, fp);

/* Close the file */
fclose (fp);

/* Do stuff */
json_object * jobj = json_tokener_parse (buffer);

...
...
...

/* Clean up */
free (buffer);

```

**edit:**

Or, to make the code slightly tidier:
```

/**
 * Read a file into memory and return its contents.
 *
 * @param filename The path to the file to read
 *
 * @return A string of the file contents, or NULL on error.
 */
char* file_read (const char* filename)
{
  FILE* fp;
  char* buffer;
  long  fsize;

  /* Open the file */
  fp = fopen (filename, "r");

  if (fp == NULL)
    {
      return NULL;
    }

  /* Get the size of the file */
  fseek (fp, 0, SEEK_END);
  fsize = ftell (fp) + 1;
  fseek (fp, 0, SEEK_SET);

  /* Allocate the buffer */
  buffer = calloc (fsize, sizeof (char));

  if (buffer == NULL)
    {
      fclose (fp);
      return NULL;
    }

  /* Read the file */
  fread (buffer, sizeof (char), fsize, fp);

  /* Close the file */
  fclose (fp);

  /* Return the buffer */
  return buffer;
}
```

Then just use file_read in your code (don't forget to free the string when done with it, though).

---

### Post by dwhitney67 on 2012-01-02
> **Barrucadu said:**
> 
Or, to make the code slightly tidier:


And even tidier so as to avoid duplicating code:
```

...
  /* Allocate the buffer */
  buffer = calloc (fsize, sizeof (char));

  if (buffer != NULL)
    {
      /* Read the file */
      fread (buffer, sizeof (char), fsize, fp);
    }

  /* Close the file */
  fclose (fp);

  /* Return the buffer */
  return buffer;
}

```

---

### Post by xtjacob on 2012-01-02
So I would implement that into my code like this?

```
#include <json/json.h>
#include <stdio.h>

void json_parse(json_object * jobj);
char* file_read (const char* filename);

int main(void) {
  char *file;
  char fname[] = "wdata.json";
  file = file_read(fname);
  json_object * jobj = json_tokener_parse(file);
  json_parse(jobj);
}

void json_parse(json_object * jobj) {
 enum json_type type;
 json_object_object_foreach(jobj, key, val) {
 printf("value: %d\n", json_object_get_int(val));
 }
}

char* file_read (const char* filename)
{
  FILE* fp;
  char* buffer;
  long  fsize;

  /* Open the file */
  fp = fopen (filename, "r");

  if (fp == NULL)
    {
      return NULL;
    }

  /* Get the size of the file */
  fseek (fp, 0, SEEK_END);
  fsize = ftell (fp) + 1;
  fseek (fp, 0, SEEK_SET);

  /* Allocate the buffer */
  buffer = calloc (fsize, sizeof (char));

  if (buffer != NULL)
    {
      /* Read the file */
      fread (buffer, sizeof (char), fsize, fp);
    }

  /* Close the file */
  fclose (fp);

  /* Return the buffer */
  return buffer;
}
```

**Edit:**
I compiled it this way, and this is what gcc says:
```
jsonparser.c: In function &#8216;file_read&#8217;:
jsonparser.c:42:3: warning: implicit declaration of function &#8216;calloc&#8217; [-Wimplicit-function-declaration]
jsonparser.c:42:12: warning: incompatible implicit declaration of built-in function &#8216;calloc&#8217; [enabled by default]

```
When I run it it prints out 
```
value: 0
value: 0
```

---

### Post by dwhitney67 on 2012-01-02
You should consider checking whether you successfully read the file; I'm not sure if the json library will handle this.  Thus consider this:
```

...
  const char* fname = "wdata.json";
  char* file = file_read(fname);

  if (file)
  {
    json_object* jobj = json_tokener_parse(file);
    json_parse(jobj);

    free(file);   /* release allocated memory */
  }

```

---

### Post by Barrucadu on 2012-01-02
You need to include stdlib.h to get calloc and free.

---

### Post by xtjacob on 2012-01-02
> **dwhitney67 said:**
> You should consider checking whether you successfully read the file; I'm not sure if the json library will handle this.  Thus consider this:
```

...
  const char* fname = "wdata.json";
  char* file = file_read(fname);

  if (file)
  {
    json_object* jobj = json_tokener_parse(file);
    json_parse(jobj);

    free(file);   /* release allocated memory */
  }

```

**Edit:**
Nevermind, I fixed it.

---

### Post by xtjacob on 2012-01-02
Okay so it compiles, but when I run it it prints
```
value: 0
value: 0

```

It's reading the file, because if I put the example json from that website it parses correctly. It doesn't parse my file correctly though... Here's my file:
```

{
	"response": {
		"version": "0.1"
		,"termsofService": "http://www.wunderground.com/weather/api/d/terms.html"
		,"features": {
		"conditions": 1
		}
	}
		,	"current_observation": {
		"image": {
		"url":"http://icons-ak.wxug.com/graphics/wu2/logo_130x80.png",
		"title":"Weather Underground",
		"link":"http://www.wunderground.com"
		},
		"display_location": {
		"full":"Allen, TX",
		"city":"Allen",
		"state":"TX",
		"state_name":"Texas",
		"country":"US",
		"country_iso3166":"US",
		"zip":"75013",
		"latitude":"33.11389923",
		"longitude":"-96.69580078",
		"elevation":"210.00000000"
		},
		"observation_location": {
		"full":"Twin Creeks/ Vistas, Allen, Texas",
		"city":"Twin Creeks/ Vistas, Allen",
		"state":"Texas",
		"country":"US",
		"country_iso3166":"US",
		"latitude":"33.112679",
		"longitude":"-96.710159",
		"elevation":"660 ft"
		},
		"estimated": {
		},
		"station_id":"KTXALLEN11",
		"observation_time":"Last Updated on January 2, 4:32 PM CST",
		"observation_time_rfc822":"Mon, 02 Jan 2012 16:32:44 -0600",
		"observation_epoch":"1325543564",
		"local_time_rfc822":"Mon, 02 Jan 2012 16:33:28 -0600",
		"local_epoch":"1325543608",
		"local_tz_short":"CST",
		"local_tz_long":"America/Chicago",
		"weather":"Clear",
		"temperature_string":"53.0 F (11.7 C)",
		"temp_f":53.0,
		"temp_c":11.7,
		"relative_humidity":"28%",
		"wind_string":"From the NNW at 5.0 MPH Gusting to 8.0 MPH",
		"wind_dir":"NNW",
		"wind_degrees":336,
		"wind_mph":5.0,
		"wind_gust_mph":"8.0",
		"pressure_mb":"1037.1",
		"pressure_in":"30.63",
		"pressure_trend":"0",
		"dewpoint_string":"21 F (-6 C)",
		"dewpoint_f":21,
		"dewpoint_c":-6,
		"heat_index_string":"NA",
		"heat_index_f":"NA",
		"heat_index_c":"NA",
		"windchill_string":"NA",
		"windchill_f":"NA",
		"windchill_c":"NA",
		"visibility_mi":"10.0",
		"visibility_km":"16.1",
		"solarradiation":"",
		"UV":"1",
		"precip_1hr_string":"0.00 in ( 0 mm)",
		"precip_1hr_in":"0.00",
		"precip_1hr_metric":" 0",
		"precip_today_string":"0.00 in (0 mm)",
		"precip_today_in":"0.00",
		"precip_today_metric":"0",
		"icon":"clear",
		"icon_url":"http://icons-ak.wxug.com/i/c/k/clear.gif",
		"forecast_url":"http://www.wunderground.com/US/TX/Allen.html",
		"history_url":"http://www.wunderground.com/history/airport/KTXALLEN11/2012/1/2/DailyHistory.html",
		"ob_url":"http://www.wunderground.com/cgi-bin/findweather/getForecast?query=33.112679,-96.710159"
	}
}
```

---

### Post by xtjacob on 2012-01-03
It seems the problem is with the JSON parser. After further research it seems that I need to specify which part of the file to open.

---

### Post by xtjacob on 2012-01-03
Alright, I got it working. Is there anyway I can call the parser from main.c to parse the file and return a value to main.c?

**main.c:**
```
/************************************************************
*                      Copyright 2012                       *
*                       Jacob Boline                        *
*************************************************************/

#include <stdio.h>
#include <curl/curl.h>
#include <string.h>
#include <stdlib.h>

void curlf(const char* url);

int main(void)
{
  char url[100] = "http://api.wunderground.com/api/59eb6f72cabe560e/"; /*Declares inital URL*/
  char location[5];
  char feature[12];
  char temp[7] = "temp_f";
  char *tempf;
  printf("Please enter your zip code:\n");                    /* Asks for location. */
  scanf("%s", location);	                                  /* Stores location. */
  printf("Please enter what information you would like:\n");  /* Asks for information. */
  scanf("%s", feature);                                       /* Stores information. */
  strcat(url, feature);                                       /* Appends feature to URL */
  strcat(url, "/q/");
  strcat(url, location);                                      /* Appends location to URL. */
  strcat(url, ".json");
  curlf(url);                                                 /* Calls cURL function. */
  printf("File downloaded.\n");
  tempf = **parser.c?**
  printf("%s\n", tempf);
}

void curlf(const char* url)
{
  CURL *json;
  FILE *wdata;
  CURLcode res;
  json = curl_easy_init();                           /* Start downloading process. */
  curl_easy_setopt(json, CURLOPT_URL, url);          /* Tells cURL what the URL is. */
  wdata = fopen( "wdata.json", "w");                 /* Create file to save data. */
  curl_easy_setopt(json, CURLOPT_WRITEDATA, wdata);  /* Tells cURL to save sata to wdata. */
  curl_easy_perform(json);                           /* Performs download. */
  curl_easy_cleanup(json);                           /* Cleans up. */
  fclose(wdata);                                     /* Close file. */
}

```

**parser.c:**
```
#include <json/json.h>
#include <stdio.h>
#include <stdlib.h>

void json_parse(json_object * jobj);
char* file_read (const char* filename);

int main(void) {
  const char* fname = "wdata.json";
  char* file = file_read(fname);
  if (file)
  {
    json_object* jobj = json_tokener_parse(file);
    json_parse(jobj);

    free(file);   /* release allocated memory */
  }
}

void json_parse(json_object * jobj) {
  jobj = json_object_object_get(jobj, "current_observation");
  jobj = json_object_object_get(jobj, "temp_f");
  float temp = json_object_get_int(jobj);
  printf("Temp is: %f degrees.\n", temp);
 
}

char* file_read (const char* filename)
{
  FILE* fp;
  char* buffer;
  long  fsize;

  /* Open the file */
  fp = fopen(filename, "r");

  if (fp == NULL)
    {
      return NULL;
    }

  /* Get the size of the file */
  fseek(fp, 0, SEEK_END);
  fsize = ftell (fp) + 1;
  fseek(fp, 0, SEEK_SET);

  /* Allocate the buffer */
  buffer = calloc (fsize, sizeof (char));

  if (buffer == NULL)
    {
      fclose (fp);
      return NULL;
    }

  /* Read the file */
  fread (buffer, sizeof (char), fsize, fp);

  /* Close the file */
  fclose (fp);

  /* Return the buffer */
  return buffer;
}
```

---

### Post by dwhitney67 on 2012-01-03
You could start by eliminating the two main() functions.  Only one is permitted within an application.

main.c:
```

#include <json/json.h>

...
const char* JSON_FILE = "wdata.json";

int main()
{
  ...
  curlf(url);

  char* file = file_read(JSON_FILE);
  if (file)
  {
    json_object* jobj = json_tokener_parse(file);
    json_parse(jobj);

    free(file);   /* release allocated memory */
  }
  return 0;
}

void curlf(const char* url)
{
  ...
  wdata = fopen(JSON_FILE, "w");                 /* Create file to save data. */
  ...
}

```
Make the changes above to your main.c file.  Remove the main() function from parser.c.  Then rebuild application as follows:
```

gcc -Wall main.c parser.c -o app

```

---

### Post by xtjacob on 2012-01-03
> **dwhitney67 said:**
> You could start by eliminating the two main() functions.  Only one is permitted within an application.

main.c:
```

#include <json/json.h>

...
const char* JSON_FILE = "wdata.json";

int main()
{
  ...
  curlf(url);

  char* file = file_read(JSON_FILE);
  if (file)
  {
    json_object* jobj = json_tokener_parse(file);
    json_parse(jobj);

    free(file);   /* release allocated memory */
  }
  return 0;
}

void curlf(const char* url)
{
  ...
  wdata = fopen(JSON_FILE, "w");                 /* Create file to save data. */
  ...
}

```
Make the changes above to your main.c file.  Remove the main() function from parser.c.  Then rebuild application as follows:
```

gcc -Wall main.c parser.c -o app

```

**EDIT: (Forgot #include <json/json.h>)**

I think I followed what you said:
**main.c:**
```
/************************************************************
*                      Copyright 2012                       *
*                       Jacob Boline                        *
*************************************************************/

#include <stdio.h>
#include <curl/curl.h>
#include <string.h>
#include <stdlib.h>
#include <json/json.h>

void curlf(const char* url);
const char* fname = "wdata.json";

int main(void)
{
  char url[100] = "http://api.wunderground.com/api/59eb6f72cabe560e/"; /*Declares inital URL*/
  char location[5];
  char feature[12];
  char temp[7] = "temp_f";
  char *tempf;
  printf("Please enter your zip code:\n");                    /* Asks for location. */
  scanf("%s", location);	                                  /* Stores location. */
  printf("Please enter what information you would like:\n");  /* Asks for information. */
  scanf("%s", feature);                                       /* Stores information. */
  strcat(url, feature);                                       /* Appends feature to URL */
  strcat(url, "/q/");
  strcat(url, location);                                      /* Appends location to URL. */
  strcat(url, ".json");
  curlf(url);                                                 /* Calls cURL function. */
  printf("File downloaded.\n");
  char* file = file_read(fname);
  if (file)
  {
    json_object* jobj = json_tokener_parse(file);
    json_parse(jobj);

    free(file);   /* release allocated memory */
  }
 return 0;
}

void curlf(const char* url)
{
  CURL *json;
  FILE *wdata;
  CURLcode res;
  json = curl_easy_init();                           /* Start downloading process. */
  curl_easy_setopt(json, CURLOPT_URL, url);          /* Tells cURL what the URL is. */
  wdata = fopen(fname, "w");                         /* Create file to save data. */
  curl_easy_setopt(json, CURLOPT_WRITEDATA, wdata);  /* Tells cURL to save sata to wdata. */
  curl_easy_perform(json);                           /* Performs download. */
  curl_easy_cleanup(json);                           /* Cleans up. */
  fclose(wdata);                                     /* Close file. */
}
```

**parser.c:**
```
#include <json/json.h>
#include <stdio.h>
#include <stdlib.h>

void json_parse(json_object * jobj);
char* file_read (const char* filename);

void json_parse(json_object * jobj) {
  jobj = json_object_object_get(jobj, "current_observation");
  jobj = json_object_object_get(jobj, "temp_f");
  char *temp = json_object_to_json_string(jobj);
  printf("Temp is: %s degrees.\n", temp);
 
}

char* file_read (const char* filename)
{
  FILE* fp;
  char* buffer;
  long  fsize;

  /* Open the file */
  fp = fopen(filename, "r");

  if (fp == NULL)
    {
      return NULL;
    }

  /* Get the size of the file */
  fseek(fp, 0, SEEK_END);
  fsize = ftell (fp) + 1;
  fseek(fp, 0, SEEK_SET);

  /* Allocate the buffer */
  buffer = calloc (fsize, sizeof (char));

  if (buffer == NULL)
    {
      fclose (fp);
      return NULL;
    }

  /* Read the file */
  fread (buffer, sizeof (char), fsize, fp);

  /* Close the file */
  fclose (fp);

  /* Return the buffer */
  return buffer;
}
```

**EDIT 2:**
Just realized I have to compile using **gcc -Wall -lcurl -l json main.c parser.c -o weather**.

---

