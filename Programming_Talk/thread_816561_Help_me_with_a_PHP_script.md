---
title: "Help me with a PHP script"
date: 2008-06-02
forum: Programming Talk
---

### Post by rakan_dr on 2008-06-02
hello everyone, 
I want your help in a PHP script.
I made like comment page for visitors to comment on articles but sometimes people write a big line which deform the look of the page. So how can I make a fixed number of characters for the script that displays the comments so when a visitor write a line its characters more than the fixed number the script puts a break automatically???

this is the code  i use:
```
<table width="800" border="0" align="right" cellpadding="0" cellspacing="0" class="table">
                      <?php do { ?>
                      <tr>
                        <td width="800"><div align="right" class="style17">
                            <p>
                              <?php
						  
						  
						   echo $row_chat['comment']; 
						   
						   
						   
						   ?>
                            </p>
                          <p align="center" class="style13">- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - </p>
                        </div></td>
                      </tr>
                      <?php } while ($row_chat = mysql_fetch_assoc($chat)); ?>
                    </table>
```
so if someone writes "444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444" the script divides it into pieces.

Thanks

---

### Post by odyniec on 2008-06-03
You can use a regular expression to insert a space after a sequence of consecutive non-whitespace characters:
```
echo preg_replace('/(\S{70})/', '$1 ', $row_chat['comment']);
```
The browser should then break lines, where necessary.

---

### Post by rakan_dr on 2008-06-03
> **odyniec said:**
> You can use a regular expression to insert a space after a sequence of consecutive non-whitespace characters:
```
echo preg_replace('/(\S{70})/', '$1 ', $row_chat['comment']);
```
The browser should then break lines, where necessary.

Pleas man can you explain the code for me???? this function is new for  me.

---

### Post by sandi.newton on 2008-06-03
> **rakan_dr said:**
> Pleas man can you explain the code for me???? this function is new for  me.
The function "preg_replace"  uses regular expression for replacing.Regular expression are used for pattern matching and substituting. Here he has tried to match 70 characters with first arg and replace them with second arg

The first argument is the pattern to search for. "\S{70}" means search for 70 occurences of letters (A-Za-z). The bracket outside it is for , i guess,clarity

The second argument is the replacement string. $1 (also known as backreference) stores the last searched string (in this case whatever \S{70} has found). So you are trying to replace 70 characters with that 70 characters plus a white space

The third argument is the string on which searching and replacing should be taken.

See php.net/preg_replace and [http://www.regular-expressions.info/tutorial.html](http://www.regular-expressions.info/tutorial.html) for more.

odyniec should correct me if i am wrong.

Hope this helps

---

### Post by Verminox on 2008-06-03
Do you want to break in the middle of a word or do you want to break in the middle of two words? If it's the latter, just fix the width of whatever HTML element contains the comment. Then the paragraph will automatically go to a new line if the content exceeds the limit.

If you you want to break in the middle of a long *word*, then do what odyniec suggested above.

---

### Post by geirha on 2008-06-03
Also, have you tried using the css [overflow](http://www.w3.org/TR/REC-CSS2/visufx.html) property?

---

### Post by odyniec on 2008-06-03
> **sandi.newton said:**
> The first argument is the pattern to search for. "\S{70}" means search for 70 occurences of letters (A-Za-z). The bracket outside it is for , i guess,clarity

Two minor corrections -- \S corresponds to any non-whitespace character, not just letters, and the bracket is there to make the matched part accessible with a back reference.

---

