---
title: "Help with jQuery (new to the language)"
date: 2009-03-30
forum: Programming Talk
---

### Post by Pyro.699 on 2009-03-30
Hello,

I basically have this setup
[html]
<html>
<head>
    <?php
    //Open Database
    // pull in the file with the database class
    require("Database.class.php");

    // create the $db ojbect
    $db = new Database("localhost", "root", "", "pokemon", "");
    $db->connect();
    ?>
<script type="text/javascript" src="jquery.js"></script>
<link rel="stylesheet" href="jquery.autocomplete.css" type="text/css" />
<script type="text/javascript" src="jquery.bgiframe.min.js"></script>
<script type="text/javascript" src="jquery.autocomplete.js"></script>
<script type="text/javascript" >
    <?php
    //#Get Names
    $sql = "SELECT `name` FROM `database`";
    $query = $db->query($sql);
    $names = "";
    while ($name = $db->fetch_array($query)) {
        $names .= $name['name']."|";
    }
    $(document).ready(function(){
       var data = "<?php echo $names; ?>".split("|");
       $("#input").autocomplete(data);
       
       $("#submit").click(function(){
           var name = $("#input").val();
           //GET NEW DATA BASED ON VALUE FROM 'name'
           //DATA SHOULD BE OBTAINED VIA MYSQL
       });
    });
</script>
</head>
<body>
<input id="input" />
<input id="submit" />
<div id="content"></div>
</body>
</html>
[/html]

Something like that... What i want to do is get information from a mysql database and display it in the div#content section.. I don't know AJAX but a friend said it involved that... Any help would be appreciated thanks :)

Please keep in mind i just learned this language today xD

Thanks
~Cody Woolaver

---

### Post by simeon87 on 2009-03-31
You can use [http://docs.jquery.com/Ajax/jQuery.post](http://docs.jquery.com/Ajax/jQuery.post) to send a POST-request to the webserver. The PHP then needs to reply with some data, like XML. In PHP you can retrieve data from the database, format it (e.g., put it in XML) and send back this response in XML. In JavaScript, you then need to process the reply and do something with it, like displaying it on the webpage.

---

### Post by Phristen on 2009-03-31
jQuery is not a language, it is a javascript framework.
If this information will not be refreshed, you don't need to ajax it, you can just load it as page loads.

But of course you need to close the ?>'s properly for any of that to work ;)

---

