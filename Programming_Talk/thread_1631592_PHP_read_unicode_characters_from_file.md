---
title: "PHP read unicode characters from file"
date: 2010-11-26
forum: Programming Talk
---

### Post by damnated on 2010-11-26
I have a file containing a list of names, some of them unicode characters (namely &#337;&#369;&#336;&#368;). I want to read these names, find them in a db and return the id associated with them. My issue is that these characters come back as ? , leading to the query not returning anything.

```

while (!feof($fh_r)) {
            $name=trim(strtolower(utf8_decode(fgets($fh_r)))); 
            $name=str_replace('.','%',$name);
            $query="SELECT id, name
                 FROM courses
                 WHERE lower(name) LIKE \"$name\"
                 ;";
                             
            $return_set=mysql_query($query,$db);
            if (! mysql_num_rows($return_set)) {
                $out.=utf8_encode($name)."<br>";
            }
            
            while ($row=mysql_fetch_array($return_set)){
                    fwrite($fh_w, $row['id']."\n");                    
                    }

        }    

<html><head><meta http-equiv="Content-type" value="text/html; charset=UTF-8" />
</head>
 <body>
  <p><?php echo $out."</p>";   
 </body>
 </html>

```All ideas are welcome ;)

---

### Post by smartbei on 2010-11-27
I don't have anyway to test this, but I would guess that strtolower is the culprit. Try printing the text before it and after it, to see if it is returning the correct values. If not, try replacing with mb_strtolower (multi byte). See [http://php.net/manual/en/function.strtolower.php](http://php.net/manual/en/function.strtolower.php)

---

### Post by damnated on 2010-11-27
```
mb_strtolower
``` has the same output. Also, if I use ```
mb_strtolower($string,'UTF-8') 
``` it deletes any accented character.

---

### Post by smartbei on 2010-11-27
Have you tried using mb_strtolower($string,'UTF-8') without doing utf8_decode?

---

### Post by damnated on 2010-11-27
Without utf8_decode i get a load of gibberish back, and it can't find even the ascii accented characters.

---

