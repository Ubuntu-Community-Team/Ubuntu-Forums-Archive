---
title: "Javascript Callbacks"
date: 2014-10-24
forum: Programming Talk
---

### Post by minerbog on 2014-10-24
Hi all,

I'm just starting to dabble in node.js and coming from a PHP, Java and C background I'm struggling with the concepts of the JavaScript callback.

Now, I understand what they are and how they are called once the function being run has completed. But it is what happens to the rest of the script I don't really get.

IE. Take this for example
```

function getDB(var) {
  run this code
  blah blah
}

function processDB(var1) {
  blah
  blah
}

getDB(var, function() {
        callback function
})

processDB(var1)

```
What I think happens is this. getDB is called and the callback waits for a respone. Straight away before getDB is finished, processDB is called?? Correct??

So I think my question is :), how does this help if certain functions required data from another one? How does function 2 know not to run yet because the data isn't back from function 1? Yes you could check that the data is returned before running function 2 but the program still goes running of into the distance in no particular order!

Am I really missing the point here???!!!  :confused:

Thanks,

Gavin

---

### Post by ofnuts on 2014-10-24
Welcome to event-driven programming(*). The point in callbacks is that you don't know/control when they run. They don't run when the function is completed (even if this can be a prereq) but when the event they are defined to process happens. Typically when you call something that uses a callback you exit the script (which allows the user to interact again with the page) right after calling it (or do little else, such as checking for errors). 

In your case, getDB() would just send a request to the server to get the data, using processDB() as the callback, and exit. processDB() will then be called when the data has been received and update the web page. Technically getDB could sent several requests in a row (to the same or different servers), using as many distinct callbacks, and each callback would update its part of the web page when the answers to the corresponding request comes back... In the case of distinct servers you'll never control in which order the page is updated.

Of course this may require some defensive programming because things can happen on the page (since control is returned to the user) between the time you send the request and the time the callback is activated).

(*) On a web page you can't have a script running continuously because it locks out user interaction. Everything that happens on the page is triggered by a user action (usually mouse clicks). The processing of these "events" may be synchronous when it is short (everything is done before returning control to the user) or asynchronous (control is returned early to the user, and an event is triggered when the work is done if there is some need to update the UI. There are of course some special events triggered without user interaction (page loaded, etc...)

---

### Post by minerbog on 2014-10-24
Thanks ofnuts,

That gives me an understanding of how the webpage uses JS, but I'm really trying to find out how the script is processed in the likes of node, where the users just pretty much requests a page and has little to do with it until it is returned to the browser. How do you know in which order the code is going to run in that instance?

Gavin

---

