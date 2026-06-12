---
title: "How to get some fields..."
date: 2008-12-12
forum: Programming Talk
---

### Post by davidtuti on 2008-12-12
Hi,

I have a text that it's:

function RunOnLoad(){var pl= 1;var nj= 0;ae('sharetabsfile1-',1);ad(0,document.getElementById('sharetemplatefile1'),1,'sharedtabsfil
einfo1-');ap(-1);switch(pl){case 4 : DoShow('mfpromo4');break;case 3 : DoShow('mfpromo3');break;case 2 : DoShow('mfpromo2');break;case 1 : d
efault : DoShow('mfpromo1');break;}  cu('**zxctsuosl5t**','**4c363225be7ee4a70ee6b948ee6686fe32df1055b9e7ee119b64923258b0150c33daf14b7fc7937**
**0e3784f4ca16161f9**','**x3lhm**');  if(fu==0&&nj==0){var nu= 4;var jc=Array();  jc[1]='/templates/linkto/default-337x281-default.html';  j
c[2]='/templates/linkto/default-729x91-default.html';  for(eh=0;eh<nu;eh++){if(document.getElementById('iframe_linkto'+eh)&&jc[eh]){
DoShow('remove_ads_button'+eh);document.getElementById('iframe_linkto'+eh).style.display="inline";if........

I would like to extract the 3 files that are in bold. I've saw that allways are after *cu('* 

Could you say me how could I do it in bash?
Many thanks and sorry for my english!

---

### Post by dwhitney67 on 2008-12-12
Repost your query, this time using some type of tag, preferably CODE or PHP.

Otherwise, your code is unintelligible.

---

### Post by davidtuti on 2008-12-12
> **dwhitney67 said:**
> Repost your query, this time using some type of tag, preferably CODE or PHP.

Otherwise, your code is unintelligible.

Well, I've modificed the text

Many thanks

---

### Post by mssever on 2008-12-12
Sensible code formatting is essential:> **davidtuti said:**
> ```

function RunOnLoad() {
    var pl= 1;
    var nj= 0;
    ae('sharetabsfile1',1);
    ad(0,document.getElementById('sharetemplatefile1'),1,'sharedtabsfileinfo1-');
    ap(-1);
    switch(pl) {
        case 4 :
            DoShow('mfpromo4');
            break;
        case 3 :
            DoShow('mfpromo3');
            break;
        case 2 :
            DoShow('mfpromo2');
            break;
        case 1 :
        default :
            DoShow('mfpromo1');
            break;
    }
    cu('**zxctsuosl5t**', '**4c363225be7ee4a70ee6b948ee6686fe32df1055b9e7ee119b64923258b0150c33daf14b7fc7937****0e3784f4ca16161f9**', '**x3lhm**');
    if(fu == 0 && nj == 0) {
        var nu = 4;
        var jc = Array();
        jc[1] = '/templates/linkto/default-337x281-default.html';
        jc[2] = '/templates/linkto/default-729x91-default.html';
        for(eh = 0; eh < nu; eh++) {
            if(document.getElementById('iframe_linkto'+eh) && jc[eh]) {
                DoShow('remove_ads_button'+eh);
                document.getElementById('iframe_linkto' + eh).style.display="inline";
                if........
```I would like to extract the 3 files that are in bold. I've saw that allways are after *cu('* 

Could you say me how could I do it in bash?
Many thanks and sorry for my english!

---

### Post by mssever on 2008-12-12
> **davidtuti said:**
> Well, I've modificed the text
But not in a helpful way. See how I modified it.
> **davidtuti said:**
> 
I would like to extract the 3 files that are in bold. I've saw that allways are after *cu('* 

Could you say me how could I do it in bash?
Many thanks and sorry for my english!
It looks like this JavaScript has been minified, which makes it difficult to decipher. Can you provide non-minified JavaScript? Also, when you're already using JavaScript, why do you want to use Bash on it? Finally, I don't see any filenames. I just see some strings passed into the cu() function.

---

### Post by davidtuti on 2008-12-12
Sorry I have a mistake. There is no files. I would like:


var1=zxctsuosl5t
var2=4c363225be7ee4a70ee6b948ee6686fe32df1055b9e7ee119b64923258b0150c33daf14b7fc79370e3784f4ca16161f9
var3=x3lhm

Many thanks,

---

### Post by mssever on 2008-12-12
> **davidtuti said:**
> Sorry I have a mistake. There is no files. I would like:


var1=zxctsuosl5t
var2=4c363225be7ee4a70ee6b948ee6686fe32df1055b9e7ee119b64923258b0150c33daf14b7fc79370e3784f4ca16161f9
var3=x3lhm

Many thanks,
Why not just modify the JavaScript to store those strings in a variable, rather than using literal strings in the function call? Or are you trying to parse information out of a web page that you don't control?

---

### Post by davidtuti on 2008-12-12
I'mtrying to parse information out of a web page that I don't control

Many thanks

---

### Post by mssever on 2008-12-12
Is the data in your first post an exact paste of a sample page? I ask because there are some odd line breaks which complicate matters considerably.

If it's not an exact paste, please post one enclosed in [noparse]```

```[/noparse] tags.

---

### Post by davidtuti on 2008-12-12
Yes.

I have these code doing a curl -L -s [http://www.xxxx.com](http://www.xxxx.com) on the terminal. The code is very long so I write a little piece of text of what I would like to have.

---

### Post by mssever on 2008-12-12
> **davidtuti said:**
> Yes.

I have these code doing a curl -L -s [http://www.xxxx.com](http://www.xxxx.com) on the terminal. The code is very long so I write a little piece of text of what I would like to have.
But did you copy and paste from the terminal, or did you redirect the output to a file? I'm asking because where the line breaks are will make a big difference, and copying from the terminal will likely corrupt your data in this case.

---

### Post by mssever on 2008-12-12
Here's a Ruby solution to get you started. The results are in the data variable. You should be able to translate this to your language of choice. Note that I assumed that all line breaks in your post were added by copying from the terminal and were not in the original.

```
#!/usr/bin/env ruby

text = <<EOT
function RunOnLoad(){var pl= 1;var nj= 0;ae('sharetabsfile1-',1);ad(0,document.getElementById('sharetemplatefi le1'),1,'sharedtabsfileinfo1-');ap(-1);switch(pl){case 4 : DoShow('mfpromo4');break;case 3 : DoShow('mfpromo3');break;case 2 : DoShow('mfpromo2');break;case 1 : default : DoShow('mfpromo1');break;} cu('zxctsuosl5t','4c363225be7ee4a70ee6b948ee6686fe32df1055b9e7ee119b 64923258b0150c33daf14b7fc79370e3784f4ca16161f9','x3lhm'); if(fu==0&&nj==0){var nu= 4;var jc=Array(); jc[1]='/templates/linkto/default-337x281-default.html'; jc[2]='/templates/linkto/default-729x91-default.html'; for(eh=0;eh<nu;eh++){if(document.getElementById('i frame_linkto'+eh)&&jc[eh]){DoShow('remove_ads_button'+eh);document.getElement ById('iframe_linkto'+eh).style.display="inline";
EOT

text =~ /cu\(([^)]+)\);/
data = $1.split(/,[ ]*/).map {|field| field[1...field.length - 1] }
puts data.inspect
```

---

### Post by davidtuti on 2008-12-12
I do copy paste but what I would like it's have the 3 fields on variables, nothing more.

Thanks

---

### Post by mssever on 2008-12-12
> **davidtuti said:**
> I do copy paste but what I would like it's have the 3 fields on variables, nothing more.

Thanks
My example gives you that. The data variable holds all three fields. data[0] holds the first, data[1] holds the second, and data[2] holds the third.

---

### Post by pp. on 2008-12-12
> **davidtuti said:**
> I do copy paste but what I would like it's have the 3 fields on variables, nothing more.

Thanks

Once you copy and paste, why don't you just search for the string cu( and  copy the part you want copied only?

---

### Post by davidtuti on 2008-12-12
> **pp. said:**
> Once you copy and paste, why don't you just search for the string cu( and  copy the part you want copied only?

Because I would like to do a shell-script.

---

### Post by davidtuti on 2008-12-12
> **mssever said:**
> My example gives you that. The data variable holds all three fields. data[0] holds the first, data[1] holds the second, and data[2] holds the third.


I would like in bash.
Thanks anyway

---

### Post by mssever on 2008-12-12
> **davidtuti said:**
> I would like in bash.
Thanks anyway
That would be somewhat difficult to do in Bash. Maybe AWK, but I don't know AWK. I'll leave the Bash translation to someone else.

---

