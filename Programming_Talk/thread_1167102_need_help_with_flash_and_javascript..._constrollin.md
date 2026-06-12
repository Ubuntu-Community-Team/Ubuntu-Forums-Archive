---
title: "need help with flash and javascript... constrolling flash animation.."
date: 2009-05-22
forum: Programming Talk
---

### Post by hockey97 on 2009-05-22
Hi, I would like to know  how I can use javascript to control a flash animation.

Well what I want to do is have the mouse be able to play the animation forward or backward.  

is this possible with javascript?  I  embeded a flash animation and need to apply javascript functions to it to check the mouse position and detect a click and hold. So when dragged to either right or left it will play the animation backwards or forwards.

---

### Post by Volt9000 on 2009-05-23
This is a bit involved, but it works-- I've done it myself once before using [Flex3](http://www.adobe.com/products/flex/) which is a free API for development Flash apps with ActionScript.

First of all, in your Flash project you have to register an externally-accessible callback function which will call a delegate in your ActionScript code. Then you use JavaScript to call this external callback function to do whatever you want.

The ActionScript code looked like this:

```

public function ClassConstructor()
{
  ExternalInterface.addCallBack("ExternalFunctionName", LocalDelegateFunction);
}

public function LocalDelegateFunction() : void
{
  // do stuff here
}

```

Then you embed the Flash project

```

<object id="uniqueObjectID">
<embed name="uniqueObjectID" src="filename.swf">
</object>

```

Then you call the function using JavaScript, thusly:

```

<script type="text/javascript">
var swfObject = document["uniqueObjectID"];
swfObject.ExternalFunctionName();
</script>

```

It took me quite a while to get all of this working properly, so if it works for you please let me know that my hard work has benefited someone else. :)

---

