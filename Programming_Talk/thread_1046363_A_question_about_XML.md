---
title: "A question about XML"
date: 2009-01-21
forum: Programming Talk
---

### Post by mikeym on 2009-01-21
Hi,

Could someone tell me what it is that's wrong with line 7 on this xml file:

```
<SearchPlugin xmlns="http://www.mozilla.org/2006/browser/search/" xmlns:os="http://a9.com/-/spec/opensearch/1.1/">
<os:ShortName>Custom</os:ShortName>
<os:Description>Custom Description</os:Description>
<os:InputEncoding>ISO-8859-1</os:InputEncoding>
<Image width="16" height="16">data:image/x-icon;base64,AAABAAEAEBAAAAEAIABoBAAAFgAAACgAAAAQAAAAIAAAAAEAIAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA7PT7/3zF6/9Ptu//RbHx/0227/+Tzvb/9vv5/97h0f9JeBz/NHoA/z98Av9AfAD/PHsA/0F6AP8AAAAA/vz7/1+33/8Mp+z/FrHw/xWy8f8bs/T/Hqrx/3zE7v////7/t8qp/zF2A/87gwH/P4ID/z59AP8+egD/Q3kA/97s8v8botj/ELn3/wy58f8PtfL/D7Lw/xuz9P8vq+f/8/n///779v9KhR3/OYYA/0GFAv88hgD/QIAC/z17AP/0+/j/N6bM/wC07/8Cxf7/CsP7/wm+9v8Aqur/SrDb//7+/v///P7/VZEl/zSJAP87jQD/PYYA/0OBBf8+fQH///3//9Dp8/84sM7/CrDf/wC14/8CruL/KqnW/9ns8f/8/v//4OjX/z+GDf85kAD/PIwD/z2JAv8+hQD/PoEA/9C7pv/97uv////+/9Xw+v+w3ej/ls/e/+rz9///////+/z6/22mSf8qjQH/OJMA/zuQAP85iwL/PIgA/zyFAP+OSSL/nV44/7J+Vv/AkG7/7trP//7//f/9//7/6/Lr/2uoRv8tjQH/PJYA/zuTAP87kwD/PY8A/z2KAP89hAD/olkn/6RVHP+eSgj/mEgR//Ho3//+/v7/5Ozh/1GaJv8tlAD/OZcC/zuXAv84lAD/O5IC/z2PAf89iwL/OIkA/6hWFf+cTxD/pm9C/76ihP/8/v//+////8nav/8fdwL/NZsA/zeZAP83mgD/PJQB/zyUAf84jwD/PYsB/z6HAf+fXif/1r6s//79///58u//3r+g/+3i2v/+//3/mbiF/yyCAP87mgP/OpgD/zeWAP85lgD/OpEB/z+TAP9ChwH/7eHb/////v/28ej/tWwo/7tUAP+5XQ7/5M+5/////v+bsZn/IHAd/zeVAP89lgP/O5MA/zaJCf8tZTr/DyuK//3////9////0qmC/7lTAP/KZAT/vVgC/8iQWf/+//3///j//ygpx/8GGcL/ESax/xEgtv8FEMz/AALh/wAB1f///f7///z//758O//GXQL/yGYC/8RaAv/Ojlf/+/////////9QU93/BAD0/wAB//8DAP3/AAHz/wAA5f8DAtr///////v7+/+2bCT/yGMA/89mAP/BWQD/0q+D///+/////P7/Rkbg/wEA+f8AA/z/AQH5/wMA8P8AAev/AADf///7/P////7/uINQ/7lXAP/MYwL/vGIO//Lm3P/8/v//1dT2/woM5/8AAP3/AwH+/wAB/f8AAfb/BADs/wAC4P8AAAAA//z7/+LbzP+mXyD/oUwE/9Gshv/8//3/7/H5/zo/w/8AAdX/AgL6/wAA/f8CAP3/AAH2/wAA7v8AAAAAgAEAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAgAEAAA==</Image>
<SearchForm>http://www.google.co.uk</SearchForm>
<os:Url type="text/html" method="GET" template="http://www.google.co.uk/search?q={searchTerms}&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-GB:unofficial&client=firefox-a">
</os:Url>
</SearchPlugin>
```

I'm trying to write a wee app that alows you to make custom searches for Firefox and I don't know what it is that's wrong with this one I've made.

---

### Post by nvteighen on 2009-01-21
That it has no child object and you're using <blah></blah> syntax instead of <blah />. You should take a look at the DTD (or better, the docs) and see how the involved object is required to work.

---

### Post by Reiger on 2009-01-21
That you're using the ampersand as a litteral. Try replacing it with &amp;

---

### Post by mikeym on 2009-01-21
Much thanks Reiger you were spot on.

And thanks nvteighen although I am using the template of an existing Firefox search plugin I'll look into it.

---

### Post by drubin on 2009-01-21
> **mikeym said:**
> Much thanks Reiger you were spot on.

And thanks nvteighen although I am using the template of an existing Firefox search plugin I'll look into it.

Just to add to his point. 

You will also need to escape.
> & 	&amp;
< 	&lt;
> 	&gt;
" 	&quot;
' 	&apos;

---

### Post by nvteighen on 2009-01-21
> **Reiger said:**
> That you're using the ampersand as a litteral. Try replacing it with &amp;
Yuck... I didn't spot that! :p

---

### Post by drubin on 2009-01-21
> **nvteighen said:**
> Yuck... I didn't spot that! :p

we all have our off days :)

---

