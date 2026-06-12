---
title: "HTML: Photo does not show in browser"
date: 2012-05-04
forum: Programming Talk
---

### Post by laserator on 2012-05-04
Hey guys,
I am having a tough time this is not really relevent to ubuntu but I know there are a bunch of smart guys on here that may be able to help. 
  I'm working on a website and there are a couple photos that I am trying to display but but they will not display in anything except for IE for windows. 
I have tried several different photo formats. I store the photos in a remote folder that links to the website and I think that may be the problem. Does anyone have a clue? here is one of the tags I am using. 

   <p><img src="file://P:/CoolStuff/mylogosbanner.bmp" alt="The my logos tab at the top menu." height="50px" width="450px"/></p>

Does anyone know some sneaky thing about chrome and gecko-based browsers that I dont know?

---

### Post by Lars Noodén on 2012-05-04
It looks like you need to resave your logo as GIF or PNG, that way it will display in the good browsers.  PNG is also an option for logos.  If it is an actual photo, then JPEG or PNG is what you want.

---

### Post by r-senior on 2012-05-04
You need to use http:// for your image, not file://. IE may understand that but it's not standard.

[https://en.wikipedia.org/wiki/File_URI_scheme](https://en.wikipedia.org/wiki/File_URI_scheme)

---

### Post by Dimarchi on 2012-05-05
It is as both Lars and r-senior say.

Let us assume some things for the sake of an example, such as your host being [www.example.com]("http://www.example.com"), your logo file saved as logo.jpg, and the html file with the link to the logo image being index.html. Furthermore, both logo.jpg and index.html are at the same file hierarchy level.

If you want to hard code your file address, you would need to write the following:
```

<p><img src="http://www.example.com/logo.jpg" alt="The my  logos tab at the top menu." height="50px" width="450px"/></p>
```If you wish to utilise relative addresses, you would write that as:
```

<p><img src="logo.jpg" alt="The my  logos tab at the top menu." height="50px" width="450px"/></p>
```

---

