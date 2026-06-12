---
title: "C++ read web page"
date: 2008-06-06
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-06-06
In Python you can read a web page via urllib

how do you do it in C++?!?


this doesn't work
[PHP]
ifstream myfile ("http://www.hello.com/index.html");
[/PHP]

So ...

---

### Post by LaRoza on 2008-06-06
That is networking. Libcurl is one of the option you have I think (but I never used it).

---

### Post by smartbei on 2008-06-07
Curl is great if you need to get data from many sites asynchronously - otherwise it might be overkill, and I am sure there are simpler solutions available.

I havent used [libwww]("http://www.w3.org/Library/") but I have seen it recommended.

---

### Post by fred.reichbier on 2008-06-07
You could also use [libcommonc++](http://www.gnu.org/software/commoncpp/) (package **libcommoncpp2-dev**), it has some useful stuff in it, and URL handlers ;)

That downloads the uri and saves in a string:
```
/** get the contents of the URI **/
std::string download_contents(std::string uri) {
	ost::URLStream url;
	char cbuf[1024];
	ost::URLStream::Error status;
	int len;
	std::string output;

	try
	{
		#ifdef DEBUG
		std::cout << "fetching " << uri << std::endl;
		#endif
		status = url.get(uri.c_str());
		if(status)
		{
			std::cout << "failed; reason=" << status << std::endl;
			url.close();
		}
		#ifdef DEBUG
		std::cout << "loading..." << std::endl;
		#endif
		while(!url.eof())
		{
			url.read(cbuf, sizeof(cbuf));
			len = url.gcount();
			if(len > 0)
				output.append(cbuf, len);
		}
		url.close();
	}
	catch(...)
	{
		std::cerr << "url " << uri << " failed" << std::endl;
	}
	return output;
}
```


Hope that's useful,

Fred

---

### Post by Mr.Macdonald on 2008-06-07
i already have libcurl3 installed so ill use it. Also it seems to come with ubuntu and i do need to parse multiple sites at once.

---

### Post by WW on 2008-06-07
FYI: [http://ubuntuforums.org/showthread.php?t=781021](http://ubuntuforums.org/showthread.php?t=781021)

---

### Post by Mr.Macdonald on 2008-06-07
Kind off topic.

how do the library makers do such low level operations, like read a website via HTTP or write to file, (please don't give me code, because i know how to write to file)


where do programmers have to write binary directly to the hard drive??

is it assembly or what?


Or does the compiler write binary that the CPU can read and execute directly e.g. is each compiled file capable of running independently, without a standard C++ library? (could i theoretically delete every file except my executable and then run it)

---

### Post by LaRoza on 2008-06-08
> **Mr.Macdonald said:**
> Kind off topic.

how do the library makers do such low level operations, like read a website via HTTP or write to file, (please don't give me code, because i know how to write to file)

where do programmers have to write binary directly to the hard drive??

is it assembly or what?

Or does the compiler write binary that the CPU can read and execute directly e.g. is each compiled file capable of running independently, without a standard C++ library? (could i theoretically delete every file except my executable and then run it)

It isn't that low level. There are low level socket programming methods, like the POSIX sockets API. One can use them to abstract tasks for more specific purposes. 

Programmers don't have to write binary at all. It is rare that assembly is used and when it is, it is with C or another language. 

The way the operating system is designed, it stands between the hardware and the programs. So, instead of writing the code to manipulate the hardware using the hardware reference manuals, it makes a system call for the operating system to do it. All programs except kernels and drivers have to talk to the kernel to do anything (usually). 

So the executables typically can't run on hardware alone, as they are build for running on the OS.

---

