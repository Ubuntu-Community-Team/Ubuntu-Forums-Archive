---
title: "Javascript - Get server page contents?"
date: 2011-04-21
forum: Programming Talk
---

### Post by cipherboy_loc on 2011-04-21
If this is in the wrong forum, please move it.

I am currently working on developing a website which will require heavy MySQL data transfer. Because I don't want to have the MySQL server face outwards, I am using PHP scripts to get content from the server. I am also using a bit of JavaScript in various parts which require the MySQL content. My question is how do I use javascript to call a php file and return the contents?

I found the following code online, but the return statement doesn't work:
```
function getCorrectPick(quad, col, row) {
    var txtFile = new XMLHttpRequest();
    var allText = "";
    txtFile.open("GET", "http://192.168.1.103/pbps/PHP5/cpicks.php?q=" + quad + "&c=" + col + "&r=" + row, true);
    txtFile.onreadystatechange = function() {
        if (txtFile.readyState === 4) {
            if (txtFile.status === 200) {
                allText = txtFile.responseText;
                return allText;
            } else {
                return "Error!";
            }
        } else {
            return "Error!";
        }
    }
    txtFile.send(null);
    return allText;
}

```

In the calling code, it calls the function, but the variable never receives the text:
```

    var result = getCorrectPick(quad, col, row);

```

An alert just after this bit reveals that result is undefined, but the value of allText (in an alert) just before returning is the desired value. What is the issue?




Cipherboy

---

### Post by smartbei on 2011-04-22
I am guessing it is some problem with conflicting variables. Could you post the whole file?

---

### Post by cipherboy_loc on 2011-04-22
Okay, so I modified the code slightly to this:
```

function getCorrectPick(quad, col, row) {
    var txtFile = new XMLHttpRequest();
    var allText = "";
    txtFile.open("GET", "http://192.168.1.103/pbps/PHP5/cpicks.php?q=" + quad + "&c=" + col + "&r=" + row, true);
    txtFile.onreadystatechange = function() {
        var state = txtFile.readyState;
        if (state === 4) {
            if (txtFile.status === 200) {
                allText = txtFile.responseText;
            } else {
                allText = "Error 200!";
            }
        } else {
            allText = "Error " + state + "!";
        }
    }
    txtFile.send(null);
    return allText;
}

```And now on the web page which it displays on, I see that the state appears to be 1 (loaded?). I read on a dated thread (wrox forum) that the use of [FONT=Courier New]onreadystatechange[/FONT] is required, but I am already using that. If I remove the test for readyState === 4, I am still unable to get the contents. 



Cipherboy

---

### Post by smartbei on 2011-04-22
Ok. It looks like you are using the asynchronous option, which means that .send() method isn't blocking. The function does indeed exit right away, before the result has returned. To test this, try putting an alert right after txtFile.send().

Perhaps what you want to do is for the caller to define a function that is passed to getCorrectPick that is called when the data arrives.

Also, it would probably be easier using some javascript framework, such as JQuery.

Note: I haven't really tried this out, but it looks like that would work. You might need to declare txtFile global (so that it will still be valid after the function exits).

---

### Post by era86 on 2011-04-22
> **smartbei said:**
> 
Also, it would probably be easier using some javascript framework, such as JQuery.


+1

You need to have some sort of callback handling capabilities when making asynchronous calls to the server.  jQuery has an excellent library for making/handling responses for such calls.

---

### Post by cipherboy_loc on 2011-04-28
End code: 

```

     $.get("/PHP/query.php", 
        function(data){
            document.getElementById(place).innerHTML = data;
    })

```Thanks all!
Cipherboy

---

