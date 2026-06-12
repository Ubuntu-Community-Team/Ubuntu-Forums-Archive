---
title: "Ubuntu unity wep apps API.. How to make my website use it???"
date: 2012-10-18
forum: Programming Talk
---

### Post by jondecker76 on 2012-10-18
I've been looking over the new 12.10 features and I'm excited about the web apps api.  I've read threough every last drop of the documentation (and I must say, the documentation is absolutely horrible).  Not one place did I see where it shows how I can make my own website use the wep apps API.

I built and maintain a website for my wife's photography business.  I wanted to integrate the administration area of this site with Ubuntu A) to make it easier for her and B) to learn how to use the API.  Even after reading the documentation, I don't even have a starting point on how to do so.  How does the browser know that my website is Ubuntu web api enabled?  Where on my web server do I store the icon file?  Is there an include I need to put into my site (built using php and mysql)?  Does anyone have a single example on how I would add features to my website with the web apps API? (for example, previous and next buttons in the media menu when vieing an online picture gallery on my website).

Again, I have read every single page in the web API documentaion, and the quick start guide.  They simply contain no information on how to do this.

Any help would be appreciated.

---

### Post by rg4w on 2012-10-18
I'm quite interested in this too, but haven't yet begun integrating my own sites, so please forgive me if the following is stuff you've already tried - I'm just guessing here, and would be very interested to learn the details of what you've tried and what has and hasn't worked thus far:

> **jondecker76 said:**
> How does the browser know that my website is Ubuntu web api enabled?
The unity.init method is described as the mechanism for this:
[http://developer.ubuntu.com/api/ubuntu-12.04/javascript/index.html](http://developer.ubuntu.com/api/ubuntu-12.04/javascript/index.html)

Did that not work for you?

> **jondecker76 said:**
> Where on my web server do I store the icon file?  
  Providing that URL appears to be part of the the unity.init method.

> **jondecker76 said:**
> Is there an include I need to put into my site (built using php and mysql)?
I don't believe so based on my reading of the API thus far, provided of course that your pages (generated or static) include the necessary JS routines to support Unity.

> **jondecker76 said:**
> Does anyone have a single example on how I would add features to my website with the web apps API? (for example, previous and next buttons in the media menu when vieing an online picture gallery on my website).
The Quick Start page has what are described as working examples of several APIs:
[http://developer.ubuntu.com/api/ubuntu-12.04/javascript/index.html](http://developer.ubuntu.com/api/ubuntu-12.04/javascript/index.html)

Again, please forgive me if you've already been through this. As a new API it may well be that its documentation is either incomplete or even incorrect.

Your guidance on what you've tried thus far will be very helpful for me as I begin exploring this, and hopefully together we'll both get our web apps working well with Unity.

---

### Post by DarkAmbient on 2012-10-18
+1, can't get it to work. Had an interest for this for quite a while now. /me subscribes to this thread

---

### Post by juancarlospaco on 2012-10-18
Do It Yourself:

```

<script>
    try {
        function unityReady() {}
        var Unity = external.getUnityObject(1.0);  
        Unity.init({name: "My Website",
            iconUrl: "http://a_nice_128px_icon.png",
            domain: "mywebiste.com",
            homepage: 'http://mywebsite.com',
            onInit: unityReady});
    } catch (err) {}
</script>

```

Let Ubuntu Do It for You:

[http://ubuntuforums.org/showthread.php?t=2003828](http://ubuntuforums.org/showthread.php?t=2003828)

---

### Post by DarkAmbient on 2012-10-19
I don't see how your code-snippet differs from any Unity webapi -tutorial. Tested it/this still.

```
<script language="Javascript">

    // print properties of the "external"-object to the console
    for(var p in external) {
        console.log(p + " = " + external[p]);
    }

    try {
    
        function unityReady() {
            console.log("Hello from unityReady()");
        }
        
        var unity = external.getunityObject(1.0);
        
        unity.init({name: "lolhost",
                    iconUrl: "http://localhost/image.png",
                    domain: "http://localhost",
                    homepage: 'http://localhost',
                    onInit: unityReady});
    } catch (e) {
        throw Error(e);            
    }
</script>
```

Added a loop to print all properties of the external-object, IDK if I've understood things wrong but shouldn't that external-object have getunityObject() as a property? 

Console tells me this below &#8595;&#8595;&#8595;

```
AddSearchProvider = function (name) {  native function NativeAddSearchProvider();  NativeAddSearchProvider(name);} unity.php:5
IsSearchProviderInstalled = function (name) {  native function NativeIsSearchProviderInstalled();  return NativeIsSearchProviderInstalled(name);} unity.php:5
Uncaught Error: TypeError: Object #<Object> has no method 'getunityObject' unity.php:22
Content script: Base content script, started on url: http://localhost/unity.php chrome-extension://pmoflmbbcfgacopiikdcpmbiellfihdg/base-content-script.js:298

```

---

### Post by DarkAmbient on 2012-10-21
Sorry for doublpost, thought I could bump this as well.

```
var unity = external.getUnityObject(1.0);
```

returns the "unityobject" in Firefox (16.0.1), so in other words it works well in Firefox! :)

external is a total different object in Chromium (22.0.1229.94) No idea why that is.. got a vanilla install of 12.10.

---

