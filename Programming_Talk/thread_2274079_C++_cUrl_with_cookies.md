---
title: "C++ cUrl with cookies"
date: 2015-04-17
forum: Programming Talk
---

### Post by Royk14 on 2015-04-17
Hi everyone!

I'm writting a c++ program that collects data from a website using **curl **and further analyses it.
I'll try not to be confusing explaining my problem:

- The program starts by reading a main webpage, lets call it **pageA**.
- From **pageA** i'm extracting the urls for another two pages, **pageB.a **and **pageB.b**. The reason why I'm doing this is because I'll want to use this program for a long time and urls for **page2a **and **page2b** change over time, whereas url for **page1** is constant.
So far so good. The two **B **pages are very similar and I manage to get all the information I want from both.
- Now, from each **B** page I'm also extracting an url to the first of a series of **C** pages, i.e., a list of data divided in several pages (it's a long table with its rows divided in several pages).
- **The problem comes now!** When I read the first of the **C** pages, instead of the page I was expecting, I receive a "blank" page (without the table I need) saying that the content is only available for browsers that support **cookies**.

Can anyone tell me how can I simulate using a browser with cookies on curl?

I don't have access to the code at this precise moment, as I am not posting from my PC, but I will update this post as soon as possible.

Additional info: the website supports login, and I am registered, but it is not necessary to be logged in in order to access any of the data I need.
Additional info: yesterday the website was denying access saying it was being accessed by a script and not by a human being (which is actually correct :P). Then I added some options to curl (don't remenber exactly which, as I don't have the code with me at the moment), but it stopped saying that and instead started complaining about the cookies.


Edit: here's the code:
> 				curl_global_init(CURL_GLOBAL_ALL);
				State::curl = curl_easy_init();
				curl_easy_setopt(State::curl, CURLOPT_USERAGENT, "Mozilla/4.0");
				curl_easy_setopt(State::curl, CURLOPT_AUTOREFERER, 1 );
				curl_easy_setopt(State::curl, CURLOPT_FOLLOWLOCATION, 1 );
				curl_easy_setopt(State::curl, CURLOPT_COOKIEFILE, "");
				curl_easy_setopt(State::curl, CURLOPT_WRITEFUNCTION, WriteCallback);
				curl_easy_setopt(curl, CURLOPT_URL, calendarUrl.c_str());
				curl_easy_setopt(curl, CURLOPT_WRITEDATA, &readBuffer);
				/*res = */curl_easy_perform(curl);
				curl_easy_cleanup(curl);



Best Regards

---

### Post by ofnuts on 2015-04-18
From a [diagonal read of this page]("http://curl.haxx.se/libcurl/c/CURLOPT_COOKIEFILE.html"), when curl receives pages the cookies in the answer are stored in the cookie jar, and when curl requests more pages it resends the cookies from the cookie jar. So:
[LIST]
[*]You shoud also have a CURLOPT_COOKIEJAR set up somewhere 
[*]The CURLOPT_COOKIEFILE should be used only once for the whole program with a name that matches the COOKIEJAR.
[/LIST]

---

