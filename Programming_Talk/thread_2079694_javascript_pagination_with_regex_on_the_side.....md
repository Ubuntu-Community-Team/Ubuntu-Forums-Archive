---
title: "javascript pagination with regex on the side...."
date: 2012-11-02
forum: Programming Talk
---

### Post by maclenin on 2012-11-02
I am trying to put together a web site pagination engine, but am running into a wee bit of trouble, near the end....

Essentially:

1. unpaginated text stored in an array
```
var A=[];
A[0]="This is a sample of text to be paginated
across a dynamically calculated number of pages.";
```
2. insert unpaginated text into a test div, with the desired pagination "aspect" left undefined (e.g. height)
```
document.write('div id="test">'+A[0]+'</div>');
```
3. evaluate undefined aspect of unpaginated text
```
testHeight=document.getElementById("test").offsetHeight;

```
4. calculate number of pages using undefined aspect / desired aspect (e.g. the final paginated height)
```
pageTotal=Math.floor(testHeight/desiredPageHeight)+1;
```

...here, the "trouble" lurks....

5. determine the total number of words in the unpaginated text sample
```
wordsNumber=A[0].match(/\S+/g).length;
```
6. define paginated text array
```
var B=[];
```
7. calculate number of words per (paginated) page
```
wordsPerPage=wordsNumber/pageTotal;
```
8. using slice and push, create the paginated array from the unpaginated array
```
for (i=0; i<pageTotal; i++) {
a=((i)*(wordsNumber/pageTotal));
b=((i+1)*(wordsNumber/pageTotal));
words=A[0].match(/\S+/g).slice(a,b);
B.push(words);
}
```
9. add paginated text elements to formatted pages (i.e. pages of desired height)
```
for (i=0; i<pageTotal; i++) {
document.write('div id="formattedPage'+i+'">'+B[i]+'</div>');
}
```
10. the **[COLOR="Red"]undesired[/COLOR]** result is (note the commas, which, among other things, prevent the text from being displayed properly on the page):

formattedPage0
```
This,is,a,sample,
```
formattedPage1
```
of,text,to,be,
```
formattedPage2
```
paginated,across,a,dynamically,
```
formattedPage3
```
calculated,number,of,pages.
```
11. the **[COLOR="DarkGreen"]desired[/COLOR]** result (which I have yet to enjoy) is the following:

formattedPage0
```
This is
a sample
```
formattedPage1
```
of text
to be
```
formattedPage2
```
paginated across
a dynamically
```
formattedPage3
```
calculated number
of pages.
```
Credit, in no small measure, for getting me this far:
[**link1**]("http://stackoverflow.com/questions/3636052/html-book-like-pagination")
[**link2**]("http://stackoverflow.com/questions/5677422/javascript-jquery-technique-paginate-fixed-size-textarea-with-overflowhidden?rq=1")
[**link3**]("http://stackoverflow.com/questions/4593565/regular-expression-for-accurate-word-count-using-javascript")

Ultimately, I'd like to be able to "slice" (or other method) up the original array (A) into elements (array B), which behave / are able to be formatted like (the) text in the original array (A)....

Thanks for any wisdom.

---

### Post by maclenin on 2012-11-02
I think I am making a bit of progress.

With reference to step 8 in the original post...

> 8. using slice and push, create the paginated array from the unpaginated array
Code:
```

for (i=0; i<pageTotal; i++) {
a=((i)*(wordsNumber/pageTotal));
b=((i+1)*(wordsNumber/pageTotal));
**[COLOR="DarkGreen"]words[/COLOR]**=A[0].match(/\S+/g).slice(a,b);
B.push(words);
}
```


...modifying the **[COLOR="DarkGreen"]words[/COLOR]** variable, by removing match and adding **split** and **join**...

```
words=A[0].**split**(" ").slice(a,b).**join**(" ");
```

...seems to deliver what I need!

Ref:
[**link4**]("http://stackoverflow.com/questions/13002346/geting-the-words-after-splitting-a-string?lq=1")

Thanks for any other thoughts or comments!

---

