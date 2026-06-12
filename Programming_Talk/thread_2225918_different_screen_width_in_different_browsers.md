---
title: "different screen width in different browsers"
date: 2014-05-24
forum: Programming Talk
---

### Post by chuchi on 2014-05-24
Hi everyone!! 
 
I am testing a mobile website with a Huawei Y530 mobile with a 480px x 854px resolution.  
 
The problem is that I am getting different widths in Android browser and Firefox browser. How is that possible?? 
 
This is just a very simple the code:
 
```
 

 
<!DOCTYPE html> 
<html> 
  <head> 
    <title></title> 
    <meta name="viewport" content="initial-scale=1.0,width=device-width"> 
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8"> 
    <style> 
 
      /* Movil portrait */ 
      @media only screen and (min-device-width : 480px)  
      { 
        body 
        { 
          background-color: red; 
        } 
      } 
    </style> 
 
    <script> 
 
      alert("width = " + screen.width); 
 
    </script> 
  </head> 
  <body> 
     
  </body> 
</html> 
 
 

```

I am just changing the background-color to red if the screen with is 480px, which is my mobile device width. It works on Android browser, but it does not in Firefox browser.

Besides, the javascript 'alert' shows 'width = 480px' in Android browser, but it shows 'width = 320px' in Firefox browser

Thank you very much!!

---

