---
title: "global variable not working within select box"
date: 2022-09-29
forum: Programming Talk
---

### Post by pizzipie on 2022-09-29
I am trying to use a dropdown box but can't get selected value outside of      $("#selbox").on('click', function (). I have tried using return but that doesn't work. Any help greatly appreciated.

R

```
  

**Place in program: <head>**

 <script type="text/javascript">
              $("#returneddatabox").hide();
**    window.myselection=""; // declare global**
    </script>

**Place in program: Just above </body>**

//  =========  dbases ==================
  

 $("#getdb").click(function ()  {

     var request = $.ajax({
        url: "getDbs-Tbls.php",
         dataType: "json"        
    });
    
    request.done(function(data) {
        for (var i=0; i<data.length; i++) {
            dbases[i]=data[i]['db'];
        }
        getChoice(dbases); ** // this function is in dropdownDB.js see below**
 
  [B]      console.log("myselection:103"+myselection);  //  output:   "myselection:103        "
        alert("myselection:104"+myselection);              //  output:   localhost - myselection:104[/B]

    }) // end request done
    
    request.fail(function (jqHR, textStatus) {
            alert("error at line 106");
        });
            


}); // end #getdb

// ========= dropdownDb.js - CREATE SELECT BOX & MAKE CHOICE  ==============

function getChoice(data) { 

    $('#dbsbox').show();
    $('#dbsbox').append($("<h4>Make Your Choice</h4>"))  // Header
                  .append("<select id='selbox' name='selbox' size='5'></select>");  // Select Box
    for (const val of data) {
        $('#selbox').append($("<option>").prop({ value: val, text: val })); // Options
    } // for
    $('#dbsbox').append("<br><br>"); 
    
     $("#selbox").on('click', function () {                       // pick choice
           ** myselection=$("#selbox option:selected").text();  **
            $('#dbsbox').hide();
             // return myselection;  // doesn't work 
            **alert( "line 23 getChoice "+myselection);  // output: "line 23 getChoice contacts"  ie: SHOWS VALUE** 
     }); // change
            **alert( "line 25 getChoice "+myselection);** ** // output: localhost - "line 25 getChoice"  **              
} // end getchoice()

//  =========================================================


    
``` 

> 
Sequence of visuals:

Start program click button "getdbases" (not shown above) Then:

alert() - localhost - "line 25 getChoice  <nothing> "
alert() - localhost - "myselection:104   < nothing> "

Make a Choice and:
[B]
alert() - "line 23 getChoice <contacts>               / / which was my choice [/B]
console:log() - "myselection:103  <nothing> 



---

### Post by &amp;KyT$0P# on 2022-09-29
My guess would be, your [FONT=Courier New]getChoice()[/FONT] function installs a click listener, but that listener is not triggered before [FONT=Courier New]getChoice[/FONT] returns.

If that is indeed the problem, one possible solution could be dropping the global [FONT=Courier New]window.myselection[/FONT] variable entirely, then make [FONT=Courier New]getChoice[/FONT] return a [Promise]("https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise") that you resolve with the value you're currently trying to store in [FONT=Courier New]window.myselection[/FONT] .  Then, where you currently call [FONT=Courier New]getChoice(dbases)[/FONT], you could do something like this (not tested, just an approximate example) -
```
getChoice(dbases).then((myselection) => {
        console.log("myselection:103"+myselection);  //  output:   "myselection:103        "
        alert("myselection:104"+myselection);              //  output:   localhost - myselection:104
});
```

---

### Post by pizzipie on 2022-09-30
Thanks for the reply. The result of that is:

[QUOTEUncaught ReferenceError: myselection is not defined
    getChoice [http://localhost/DBases.com/Dbmysql/experiment/js/dropdownDB.js:26](http://localhost/DBases.com/Dbmysql/experiment/js/dropdownDB.js:26)
    <anonymous> [http://localhost/DBases.com/Dbmysql/experiment/dbConnect.html:106](http://localhost/DBases.com/Dbmysql/experiment/dbConnect.html:106)
    jQuery 6
    <anonymous> [http://localhost/DBases.com/Dbmysql/experiment/dbConnect.html:92](http://localhost/DBases.com/Dbmysql/experiment/dbConnect.html:92)
    jQuery 9
    <anonymous> [http://localhost/DBases.com/Dbmysql/experiment/dbConnect.html:90](http://localhost/DBases.com/Dbmysql/experiment/dbConnect.html:90)
    jQuery 13][/QUOTE]

---

### Post by &amp;KyT$0P# on 2022-09-30
What is the code of your newly-modified [FONT=Courier New]getChoice()[/FONT] function?  Did you need to modify my example code for the place where you call [FONT=Courier New]getChoice(dbases)[/FONT]?

Without seeing the changed code, no way to know why it's erroring.

---

### Post by pizzipie on 2022-09-30
Thanks halogen2,

I put everything in the #selbox.on(click ... , like so:

```

// ========= CREATE SELECT BOX & MAKE DATABASE CHOICE  ==============

function getDbChoice(data) { 

    $('#dbsbox').show();
    $('#dbsbox').append($("<h4>Choose a Database</h4>"))  // Header
                  .append("<select id='selbox' name='selbox' size='5'></select>");  // Select Box
    for (const val of data) {
        $('#selbox').append($("<option>").prop({ value: val, text: val })); // Options
    } // for
    $('#dbsbox').append("<br><br>"); 
    
[B]     $("#selbox").on('click', function () {                       // pick choice
            myselection=$("#selbox option:selected").text();  
            $('#dbsbox').empty();  //.hide();
        
        var request = $.ajax({
        url: "getTbls.php",
        type:"GET",
        data: {"dbase":myselection},
         dataType: "json" 
  }); // request

request.done(function (data) {
    
        getTblChoice(data);     // go get the associated table [/B]
});        
        
}); // selbox click
                            
} //getDbChoice()


```

This works just fine. Again thanks for the help!!

---

