---
title: "Calling a function in javascript"
date: 2008-03-04
forum: Programming Talk
---

### Post by mohtasham1983 on 2008-03-04
Hi,

I've been working with YUI (Yahoo user Interface) javascript library for a while without much knowledge about Javascript itself. However, I have learned a lot about javascript when working with YUI.

Yesterday, I came across something that I wanted to do with javascript so that I don't need to rewrite a function again.

I have a function which i found in YUI examples like this which does its job very fine:

[PHP]
YAHOO.util.Event.addListener(window, "load", function() {
    YAHOO.example.Local_XML = new function() {
...
...
...
...
    };
});  [/PHP]

As you can see once the page is loaded this function is executed. Now, what I'm looking for is to find a way of calling the same function again in another event outside my function.

For example I have the following function:

[PHP]
function new_function() {
      ....
       ...
      I need to call YAHOO.example.Local_XML function and its method in here

}
[/PHP]
I would be very glad if somebody let me know how this feature of javascript works and give me some guide lines about it.

Thanks

---

### Post by LaRoza on 2008-03-04
The syntax "= function(){}" or "= new function(){}" are anonymous, and cannot be called by name, which is their point. They the are meant to be single use functions, like lambda's.

You can just trigger the event again to call it, or put the function in an named function and just call that function for both events.

---

### Post by mohtasham1983 on 2008-03-04
Thanks, it was really helpful. I just made it as a simple function and it worked fine.

I just don't know why yahoo developers used that in their example page.

---

### Post by LaRoza on 2008-03-04
> **mohtasham1983 said:**
> Thanks, it was really helpful. I just made it as a simple function and it worked fine.

I just don't know why yahoo developers used that in their example page.

Most events use anonymous functions. That is where you will see them most often.

In my experience, most of the time you don't use the same function for different events, so it works fine.

---

### Post by mohtasham1983 on 2008-03-04
In my case I have a div element which will be filled by a datatable whose data is retrieved from an xml file in the load event.

Inside the datatable I have a button which deletes one of the xml elements. I just needed to call the same function to retrieve data from xml document after that element was deleted without loading the entire page again.

---

