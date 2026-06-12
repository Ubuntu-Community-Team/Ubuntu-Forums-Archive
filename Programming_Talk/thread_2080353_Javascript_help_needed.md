---
title: "Javascript help needed"
date: 2012-11-03
forum: Programming Talk
---

### Post by ironic.demise on 2012-11-03
I've recently gotten a Raspberry pi and I am using it to learn some web development.
I've set up Apache on it, with PHP and MySql although I'm not using MySql yet.
in the gallery I have php showing every image in the /gallery folder with the following code.
```

<img onclick="function(imagename)" src=/gallery/image>

```here's my javascript function
```

function frame(variable){
document.getElementById('frame').innerHTML = '<img src="/gallery/' + variable + '">';
}

```I've been messing around in W3Schools tryme windows and I'm quite confused as how I'm supposed to get this to work...

Can somebody tell me a few things.

Am I passing the variable along correctly?
Am I using document.getElementById correctly?
Am I using .innerhtml correctly?

How I have it set up currently is
```

function frame(){
code;
}

<div id=frame></div>

<img onclick="function(image)" src="image">

```the url this can be accessed at currently, providing there's nothing wrong with my apache setup [http://unacquainted.dnsdynamic.com/gallery.php](http://unacquainted.dnsdynamic.com/gallery.php)

The images are passed through PHP, so the code is a mess right now.

---

### Post by ironic.demise on 2012-11-03
Another thing that might be useful is this

```

<script>
function test(var1)
{
document.getElementById('test').innerHTML = "hello";
}
</script>

<p id="test">Content should change</p>

<button type="button" onclick="test()">test</button>

```The above works, however as soon as I add args, nothing works?
i.e.
```

onclick="test(arg)"

```

After testing further, I don't know how to pass an argument from an onclick?

---

### Post by zoopside on 2012-11-03
Hi there,
I don't understand exactly what you're after, but can hopefully help out a bit. Starting with this code :

<img onclick="function(image)" src="image">

The onclick handler doesn't pass any variable(s) which you don't explicitly define. So the "image" in this case will not be passed, and will be an undefined variable. You could instead do :

<img onclick="function('usefulVariable')" src="image">

to pass 'usefulVariable into your function.

Also, in this function :

function test(var1)
{
document.getElementById('test').innerHTML = "hello";
}

you aren't doing anything with var1, so even if you passed a variable in to it, nothing different would happen when it's executed. You could instead do something like:

function makeIdSayHello(id)
{
document.getElementById(id).innerHTML = "hello";
}

<div id="myDiv" onclick="makeIdSayHello('myDiv')" />

Although this :
document.getElementById(id).innerHTML = "hello";

is a bit dangerous as you should check to see that you've successfully retrieved the element prior to accessing the innerHTML. So :

var ele = document.getElementById(id);
if (ele) {
    ele.innerHTML = "hello";
}

Hope that helps a bit.

---

### Post by ironic.demise on 2012-11-03
> **zoopside said:**
> Hi there,
I don't understand exactly what you're after, but can hopefully help out a bit. Starting with this code :

<img onclick="function(image)" src="image">

The onclick handler doesn't pass any variable(s) which you don't explicitly define. So the "image" in this case will not be passed, and will be an undefined variable. You could instead do :

<img onclick="function('usefulVariable')" src="image">

to pass 'usefulVariable into your function.

Also, in this function :

function test(var1)
{
document.getElementById('test').innerHTML = "hello";
}

you aren't doing anything with var1, so even if you passed a variable in to it, nothing different would happen when it's executed. You could instead do something like:

function makeIdSayHello(id)
{
document.getElementById(id).innerHTML = "hello";
}

<div id="myDiv" onclick="makeIdSayHello('myDiv')" />

Although this :
document.getElementById(id).innerHTML = "hello";

is a bit dangerous as you should check to see that you've successfully retrieved the element prior to accessing the innerHTML. So :

var ele = document.getElementById(id);
if (ele) {
    ele.innerHTML = "hello";
}

Hope that helps a bit.
Thanks, I'm just starting with JS and it's always useful to see how things *should* be done as opposed to just hacking it.

I'll be sure to adopt the safety check with if.

long story short, I've made a gallery that just shows a bunch of thumbnails, I want this javascript to show the full image at the top when it is clicked.

The variable I want to pass is the image name so the javascript knows which one to show.

I will take a look at your code and see if I can pass along the image name, and I know how to use it in the javascript.



Just tried that, works perfectly, the problem was what you thought, I wasn't using the syntax properly.

---

