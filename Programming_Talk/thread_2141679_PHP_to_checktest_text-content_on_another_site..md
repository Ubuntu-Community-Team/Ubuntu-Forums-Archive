---
title: "PHP to check/test text-content on another site."
date: 2013-05-03
forum: Programming Talk
---

### Post by Valpskott on 2013-05-03
I'm new to PHP, I'm creating a page where people can upload zip/rar-files, and I'd be happy to receive some help. And I hope it will be a fun challange to someone who knows the ins and out's of php. For this, I have a form with 3 text fields, 1 button for file browsing, and one send/submit button.

What I want is, for these 3 text fields to hold the send/submit-button hostage (preferably grayed out until the fields are filled out).

One of the fields is an input for youtube-account name, so, I'd like the page to check "http://www.youtube.com/user/$USERINPUT" if the page contains the text "404 Not Found".
This check should be performed "live".

So far, the code looks like this.

```

<?php include("head.php"); ?>

<div id='cssfield1'>

<?php
if($_FILES["zip_file"]["name"]) {
        $filename = $_FILES["zip_file"]["name"];
        $source = $_FILES["zip_file"]["tmp_name"];
        $type = $_FILES["zip_file"]["type"];
        $map = $_POST["map"];
        $youtube = $_POST["youtube"];
        $email = $_POST["email"];

        $name = explode(".", $filename);
        $accepted_types = array('application/x-rar-compressed', 'application/octet-stream', 'application/zip', 'application/x-zip-compressed', 'multipart/x-zip', 'application/x-compressed');
        foreach($accepted_types as $mime_type) {
                if($mime_type == $type) {
                        $okay = true;
                        break;
                }
        }

        $continue = strtolower($name[1]) == 'zip' ? true : false;
        if(!$continue) {
                $message = "Filen du försöker ladda upp är inte en zip eller rar-fil. Försök igen.";
        }

        $target_path = "/home/valpskott.se/CUSTOM/".$filename;
        if($okay == true) {
                if(move_uploaded_file($source, $target_path)) {
                        $map = preg_replace("/[\s_]/", "ZPACE", $map);
                        $map = preg_replace("/[^a-öA-Ö0-9\s.]/", "", $map);
                        $youtube = preg_replace("/[\s_]/", "ZPACE", $youtube);
                        $youtube = preg_replace("/[^a-öA-Ö0-9\s.]/", "", $youtube);
                        $filename = preg_replace("/[\s_]/", "ZPACE", $filename);
                        $filename = preg_replace("/[^a-öA-Ö0-9\s.]/", "", $filename);
                        exec ("CUSTOM/unpack.sh $map $youtube $filename $email");
                        $message = "Din fil har laddats upp och processats.";
                } else {
                        $message = "Det uppstod problem med din uppladdning. Försök igen.";
                }
        }
}
?>

<form enctype="multipart/form-data" method="post" action="">
<label for="map">Mappens namn:</label><br>
<input type="text" name="map" id="map"><br>

<label for="youtube">Ditt användarnamn på Youtube:</label><br>
<input type="text" name="youtube" id="youtube"><br>

<label for="email">E-post:</label><br>
<input type="text" name="email" id="email"><br>

<label>Fil:</label><br> <input type="file" name="zip_file" />
<br />
<input type="submit" name="submit" value="Skicka" />
</form>

<?php if($message) echo "<p>$message</p>"; ?>

</div>

</center>
</body>
</html>

```

Any help or pointers is much appreciated.

---

### Post by epicoder on 2013-05-04
It would be a lot simpler and easier on your server to do this  verification client side. If your visitors are going to be using modern  browsers, simply add the "required" attribute to your input tags.
HTML syntax:
```
<input type="text" name="email" id="email" required>
```
XHTML syntax:
```
<input type="text" name="email" id="email" required="required" />
```

To  check the existence of a youtube user, use the developer API.  (documented  [here]("https://developers.google.com/youtube/2.0/developers_guide_protocol_profiles#Profiles"))
If you're using jQuery, here's how you would check if a user exists:
```
//assuming form is a jQuery node of the form in question...
form.submit(function (event) {
    try {
        $.ajax({
            url: "http://gdata.youtube.com/feeds/api/users/" + $("#youtube").val(),
            dataType: "text",
            method: "GET",
            cache: false,
            statusCode: {
                404: function () {
                    throw new Error();
                }
            }
        }).fail(function () {
            throw new Error();
        }).done(function (data) {
            if (data === "User not found") {
                throw new Error(); //just in case youtube doesn't 404 for some reason
            }
        });
    } catch (e) {
        event.stopPropogation();
        event.preventDefault();
        //user not found, handle it how you like here...
        return false;
    }
    //if control falls through to here, then the user is valid.
    return true;
});
```

One more thing... your html is a mix of XHTML (<emptyelem booleanattr="booleanattr" />) and HTML (<emptyelem booleanattr>) syntax. While this generally isn't a problem, it might be in the future and should be avoided. Both are valid, so pick whichever you like better and use it consistently throughout your code.

---

### Post by Bufeu on 2013-05-06
Valpskott, it's fun to see some Swedes here! :D
This should work:
[HTML]<input type="text" name="email" id="email" required>[/HTML]
Edit: saw that **epicoder** proposed exactly the same solution that I did. #-o

---

### Post by Valpskott on 2013-05-07
Thanks for your suggestions. The "required" stuff solved one of the problems, thank you both for that.

I havn't been able to figure out where to insert epicoders jquery script. My friend is comming over this weekend, so, he will help me implement that solution. Again, thanks (tack) both of you! :)

---

### Post by Bufeu on 2013-05-07
Ingen orsak. ;)
Glad you found a solution.

---

### Post by SeijiSensei on 2013-05-07
If you just want to check the validity of the YouTube URL, you can use the curl functions, or use the fopen() command if you have [allow_url_open](http://www.php.net/manual/en/filesystem.configuration.php#ini.allow-url-fopen) enabled.  fopen("http://www.example.com","r") will return a file pointer resource if the site exists or FALSE if it does not.

---

