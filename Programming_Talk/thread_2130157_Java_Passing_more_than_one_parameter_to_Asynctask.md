---
title: "Java: Passing more than one parameter to Asynctask?"
date: 2013-03-28
forum: Programming Talk
---

### Post by fallenshadow on 2013-03-28
Hi all,

I have been looking up this topic for a while but can't come across any simple tutorial/explaination. 

All I want to do is pass a filename into a Asynctask for downloading files. Here is my Asynctask setup currently:

```

private class DownloadFile extends AsyncTask<String, Integer, String> {
	    @Override
	    protected String doInBackground(String... sUrl) {
	        try {
//download files etc...


```

Anyone have experience doing this?

---

### Post by KdotJ on 2013-03-28
Just pass in a file name?

You've already got it... just call it like:

```
new DownloadFile().execute("yourFilename");
```

It just uses varargs ([http://docs.oracle.com/javase/1.5.0/docs/guide/language/varargs.html](http://docs.oracle.com/javase/1.5.0/docs/guide/language/varargs.html))

The Android docs give you a typical example

[http://developer.android.com/reference/android/os/AsyncTask.html](http://developer.android.com/reference/android/os/AsyncTask.html)

---

### Post by fallenshadow on 2013-03-29
I don't think I have it already. 

What im currently doing is passing in a URL but I also want to pass in a filename as a second parameter.

> new DownloadFile().execute("yourFilename");

Doing this will just make it take the parameter as a URL.

---

### Post by KdotJ on 2013-03-29
Ah ok, I thought you were using the URL for the filename (e.g. "http://someurl.com/<filename>") but you want to pass in the URL separate from the filename?

So there are two things that come to mind....

1) Just simply supply two String arguments into the method call, and just know that they should be URL and file name. Varargs will allow this...

In the task:
```

@Override
protected String doInBackground(String... args) {
    // args[0] will be the URL
    // args[1] will be the filename
}
```


Call it by:
```
new DownloadFile().execute("the url", "the filename");
```



2) If there will only be one URL (or one filename) per task, then have an instance variable in your task which stores the value and pass it to the constructor.

In the task:
```

private class DownloadFile extends AsyncTask<String, Integer, String> {

    private final String url;

    DownloadFile(final String url) {
        this.url = url;
    }

    @Override
    protected String doInBackground(String... args) {
        // use this.url for the URL
        // use args[0] for the filename
    }

   ....
}

```

Call it by:
```
new DownloadFile("the url").execute("filename");
```

There are probably many other ways too...

Hopefully I've understood what you're after

---

### Post by fallenshadow on 2013-03-30
Thanks!

It does work the same as args pretty much. I thought it was more complicated than that!

So this solves the filename but also how can I use the same code to download multiple files? 

I can provide more arguments but it will always take arg0 and arg1. I tried a for loop but that caused my code to crash. :/

---

### Post by KdotJ on 2013-03-30
Without looking at the rest of the code it's hard to say the best way to achieve what you want.

> **fallenshadow said:**
> how can I use the same code to download multiple files? 

- Are all of the files at the same URL?
- Do you want to download these files concurrently?
- Can you just use the fully qualified filename? (e.g. "http:/remote.server:1200/path/to/file")

If all of the files are at the same URL, then I would personally suggest you use something like in my option 2) from the post above. This means the URL will be the same for the entire lifetime of your AsyncTask and you just give it the filenames when you call execute().

If you want (or can) download the files concurrently, then maybe think about using a separate DownloadTask for each file.


> **fallenshadow said:**
> I can provide more arguments but it will always take arg0 and arg1. I tried a for loop but that caused my code to crash. :/

Again, without looking at the code it's hard to say.

A for-loop for multiple args could look like:

```

for (int i = 0; i < args.length; i+=2) {
    // args[i] is the URL
    // args[i+1] is the filename
}
```

---

### Post by fallenshadow on 2013-03-30
Excellent! I did a loop before but I didn't use it in the right place. I also found out saving files was missing a "/". :D

I appreciate you helping me out with both issues I was having! Thanks again!

---

### Post by KdotJ on 2013-03-31
Good stuff, hope the rest of the app goes well!

---

