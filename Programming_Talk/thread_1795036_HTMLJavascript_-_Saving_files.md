---
title: "HTML/Javascript - Saving files"
date: 2011-07-01
forum: Programming Talk
---

### Post by slooksterpsv on 2011-07-01
I'm working on an editor, kind of like BeSpin, using javascript and html5.

I have a few questions:

1. How could I output the content of a variable that is storing text, to a file using Javascript or is it even possible?

2. If I can't do it with JS, can I do it with another language that wouldn't require a server for processing?

---

### Post by roccivic on 2011-07-02
The quick answer here is: no and no. JS or any other client-side scripting languages cannot write to files directly AFAIK. So you'll need a server for this.

Anyway, where do you want to save this data? On the server or on the user's computer? I'm guessing the latter...


Here's a simple example of the case where you want the user to download the text using PHP and jQuery. Note that this is quite roundabout, since the data is sent to the server and then sent back to the user, so there is a waste of a round-trip over the network.

[PHP]<?php
if (! empty($_GET['save']) && ! empty($_GET['data'])) {
    header('Content-type: text/plain');
    header('Content-Disposition: attachment');
    echo $_GET['data'];
    die;
}
?>
<html>
    <head>
        <script type="text/javascript" src="http://ajax.googleapis.com/ajax/libs/jquery/1.6.1/jquery.min.js"></script>
        <script type="text/javascript">
            var string = "Hello World";
            $(document).ready(function () {
                $('button').click(function () {
                    location.href = 'test.php?save=1&data=' + encodeURI(string);
                });
            });
        </script>
    </head>
    <body>
        <button>Download Variable</button>
    </body>
</html>
[/PHP]


For saving on the server you will need a combination of JS and any server-side scripting language.

Here's a simple example in jQuery and PHP using AJAX for case 1 (saving to server):
[PHP]<?php
if (! empty($_GET['save']) && ! empty($_POST['data'])) {
    // do something with $data, save to filesystem for example:
    // file_put_contents('myfile.txt', $data);
    echo 'OK';
    die;
}
?>
<html>
    <head>
        <script type="text/javascript" src="http://ajax.googleapis.com/ajax/libs/jquery/1.6.1/jquery.min.js"></script>
        <script type="text/javascript">
            var string = "Hello World";
            $(document).ready(function () {
                $('button').click(function () {
                    $.post('test.php?save=1', {'data' : string}, function (data) {
                        var responce = "The upload failed";
                        if (data == 'OK') {
                            responce = "The upload succeded";
                        }
                        alert(responce);
                    });
                });
            });
        </script>
    </head>
    <body>
        <button>Upload Variable</button>
    </body>
</html>
[/PHP]

---

### Post by juancarlospaco on 2011-07-02
Server side, you can make an "Save" button and it downloads a PDF or TXT file i think...

---

### Post by ProntoAnthony on 2011-07-02
You can actually use the new [w3C File API]("http://www.w3.org/TR/FileAPI/") to directly read  desktop files but that may be too limited for your needs. No write or save command is included.

---

### Post by cgroza on 2011-07-02
Wouldn't accessing files via Javascript be a security risk?
Anyone could put a malicious script in an obscure website...

---

### Post by slooksterpsv on 2011-07-02
Yeah that's true. Hmm... I'll have to see if I can use the LocalStorage object for those needs then.

Thanks everyone =D

---

