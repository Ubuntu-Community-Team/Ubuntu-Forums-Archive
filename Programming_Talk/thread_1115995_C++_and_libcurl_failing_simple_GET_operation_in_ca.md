---
title: "C++ and libcurl failing simple GET operation in callback function"
date: 2009-04-04
forum: Programming Talk
---

### Post by kvolden on 2009-04-04
Hi, I've been googling for the last two hours without finding the answer to this problem.. I'm using libcurl in a C++ application, and at first I tried without the callback function, which provided the html to the standard output. That worked fine, but when I try to utilize the callback function, as far as I can tell pretty much exactly like the documentation and other confirmed working examples, something goes off the hinges. After a little investigation, I could see that the variable "size_t nmemb" gets a value of "3213310828", and "size_t size" a value of "751"..

The documentation claims that the total size of the received file is size*nmemb, which in my case is obviously wrong, as the real file size is 272413 bytes.

Here's the relevant code:
```

void Book::update(){

	CURL *curl;
	CURLcode result;
	std::string url;
	std::string html = "";
	
	
	url = "http://www.amazon.co.uk";
	curl = curl_easy_init();

	if(curl){
		curl_easy_setopt(curl, CURLOPT_URL, url.c_str());
		curl_easy_setopt(curl, CURLOPT_WRITEFUNCTION, &Book::write_html);
		curl_easy_setopt(curl, CURLOPT_WRITEDATA, &html);
		result = curl_easy_perform(curl);
		curl_easy_cleanup(curl);
	}
}

size_t Book::write_html(char *buffer, size_t size, size_t nmemb, std::string *html){
	int result = 0;
	
	if(buffer != NULL){
		html->append(buffer, size*nmemb);
		result = size*nmemb;
	}
	return result;
}

```

Any help will be highly appreciated! Thanks.

---

### Post by kvolden on 2009-04-06
Nevermind. I got it to work. The problem was with C vs C++ object functions, and the "hidden" object pointer which is passed in C++.

The solution was to declare the function as static in the header file, and I also changed "std::string *html" to "void *ptr" in the declaration, with an in-function cast to string pointer. Don't know if the last one made any difference, but it works anyway.

---

### Post by indraginanjar on 2010-09-03
You're such a great help to get a quick start with libcurl.
Thank you.

---

### Post by James78 on 2010-09-03
> **indraginanjar said:**
> You're such a great help to get a quick start with libcurl.
Thank you.

In case you're curious, here's my code for the writeback function. It doesn't require setting the function to static.

```
const string url = "url";
string data;

curl_easy_setopt(cHandle, CURLOPT_URL, url.c_str());
curl_easy_setopt(cHandle, CURLOPT_WRITEFUNCTION, writeToString);
curl_easy_setopt(cHandle, CURLOPT_WRITEDATA, &data);
res = curl_easy_perform(cHandle);

// data now holds response

// write curl response to string variable..
size_t writeToString(void *ptr, size_t size, size_t count, void *stream)
{
    ((string*)stream)->append((char*)ptr, 0, size* count);
    return size* count;
}
```

---

