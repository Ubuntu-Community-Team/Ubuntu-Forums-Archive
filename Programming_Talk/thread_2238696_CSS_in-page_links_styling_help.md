---
title: "CSS in-page links styling help"
date: 2014-08-09
forum: Programming Talk
---

### Post by DaveNelson on 2014-08-09
Hello,

I am teaching myself the fine art of web page development using HTML5 and CSS3. I have developed pages that so far do almost everything that I want, but I've run into one speed-bump that I can't seem to overcome. Apologies in advance if my terminology is incorrect.

I have a wrapper div that contains all of the content, with a fixed header div at the top of the page, two columns below that, one floated left, fixed, and ~20% wide, and a static one next to it that takes up the rest of the wrapper width. Finally there is a static page footer. This all looks something like:

```
+----------------------------------------+
| +------------------------------------+ |
| |            page_header             | |
| +------------------------------------+ |
| +-----++-----------------------------+ |
| |     || detail1                     | |
| |     ||    sub_detail1              | |
| |side_|| ...                         | |
| |menu ||                             | |
| |     ||                             | |
| |     ||      main_content           | |
| |     ||                             | |
| +-----||                             | |
|        | ...                         | |
|        | detailx                     | |
|        |    sub_detailx              | |
|        +-----------------------------+ |
| +------------------------------------+ |
| |            page_footer             | |
| +------------------------------------+ |
|               wrapper                  |
+----------------------------------------+
```

So the page header and the side menu are fixed, and the main content and footer are allowed to scroll when the main content is taller than the page. Relevant CSS and HTML follows below.

The problem I have run into involves in-page links for main content items. In the main content area I have several paragraphs of detail text, some with sub_detail text below. If I create an in-page link to a species' detail paragraph, and follow that link, the detail text is positioned at the top of the browser window, at the same height as the top of the page header.

So my questions are: how can I make that text appear below the header instead of even with it when jumping to it? Or am I trying to do something that is not easily done?

Regards,
Dave

The CSS:
```

*
{
   margin:                   0;
   padding:                  0;
}

html
{
   color:                    #000000;
   font-size:                100%;
}

body
{
   background-color:         #666666;
   font-family:              "Times Roman", serif;
   font-size:                62.5%;
}

.detail
{
   font-size:                1.5em;
   font-style:               normal;
}

.detail_wrapper
{
   margin-bottom:            1em;
   margin-left:              2.7em;
}

.menu_wrapper
{
   margin-left:              1em;
   width:                    18em;
}

.side_nav
{
   font-size:                1.25em;
}

.sub_detail
{
   padding-left:             2em;
   font-size:                1.5em;
}

#main_content,
#side_menu
{
   float:                    left;
   margin-top:               10.5em;
   min-height:               35em;
}

#main_content
{
   margin-bottom:            1em;
   margin-left:              20em;
   margin-top:               10em;
   width:                    67.5em;
}

#main_content h1
{
   border-bottom-color:      #000000;
   border-bottom-style:      solid;
   border-bottom-width:      0.05em;
   font-size:                3em;
   padding-bottom:           0.10em;
}

#main_content h2
{
   font-size:                2.5em;
}

#main_content h3
{
   font-size:                2em;
   margin-left:              -1.3em;
}

#page_foot
{
   border-top-color:         #000000;
   border-top-style:         solid;
   border-top-width:         0.1em;
   clear:                    both;
   font-size:                2em;
   padding-top:              1em;
   text-align:               center;
}

#page_head
{
   background-color:         #FFFFFF;
   background-image:         url(./fadedown.png);
   border-bottom-color:      #000000;
   border-bottom-style:      solid;
   border-bottom-width:      0.2em;
   height:                   10em;
   margin-bottom:            0.1em;
   position:                 fixed;
   text-align:               center;
   width:                    90em;
}

#page_head h1
{
   font-size:                5em;
}

#page_head h2
{
   font-size:                2.5em;
}

#side_menu
{
   position:                 fixed;
   width:                    20em;
}

#wrapper
{
   background-attachment:    fixed;
   background-color:         #FFFFFF;
   background-image:         url(./fadedown.png);
   background-repeat:        repeat-x;
   margin-left:              auto;
   margin-right:             auto;
   min-height:               45em;
   width:                    90em;
}
/*
 * fadedown.png is a 1 pixel wide, 1200 pixel tall transparent image
 * that starts at 0% blue at the top, and darkens to 90% blue at the
 * bottom.
*/
```

The HTML:
```
<!DOCTYPE html>
<html lang="en">
   <head>
      <meta name="Author" content="D. Nelson" >
      <meta charset="UTF-8">
      <meta name="description" content="testing boxes" >
      <title>
         box layout test
      </title>
      <link rel  = "stylesheet"
            id   = "resume.css"
            href = "./page.css"
            type = "text/css"
      >
   </head>
   <body>
      <div id="wrapper">
         <div id="page_head">
            <h2>Sub&ndash;Title</h2>
            <h1>Main Title</h1>
         </div> <!-- End of the page_head container -->

         <div id="main_content">
            <h1>Content Title </h1>
            <h2 id="detail1">Detail1</h2>
            <div class="detail_wrapper">
               <p class="detail">
                  Lorem ipsum dolor sit amet, consectetuer adipiscing
                  elit. Aenean commodo ligula eget dolor. Aenean massa. Cum
                  sociis natoque penatibus et magnis dis parturient montes,
                  nascetur ridiculus mus. Donec quam felis, ultricies nec,
                  pellentesque eu, pretium quis, sem. Nulla consequat massa
                  quis enim.  Donec pede justo, fringilla vel, aliquet nec,
                  vulputate eget, arcu. In enim justo, rhoncus ut, imperdiet a,
                  venenatis vitae, justo. Nullam dictum felis eu pede mollis
                  pretium. Integer tincidunt. Cras dapibus. Vivamus elementum
                  semper nisi. Aenean vulputate eleifend tellus. Aenean
                  leo ligula, porttitor eu, consequat vitae, eleifend
                  ac, enim. Aliquam lorem ante, dapibus in, viverra quis,
                  feugiat a, tellus. Phasellus viverra nulla ut metus varius
                  laoreet. Quisque rutrum. Aenean imperdiet. Etiam ultricies
                  nisi vel augue. Curabitur ullamcorper ultricies nisi. Nam
                  eget dui.
               </p>
                  <p class="sub_detail">sub&ndash;detail1</p>
                  <p class="sub_detail">sub&ndash;detail2</p>
                  <p class="sub_detail">sub&ndash;detail3</p>
            </div>
            <h2 id="detail2">Detail2</h2>
            <div class="detail_wrapper">
               <p class="detail">
                  Etiam rhoncus. Maecenas tempus, tellus eget condimentum
                  rhoncus, sem quam semper libero, sit amet adipiscing
                  sem neque sed ipsum. Nam quam nunc, blandit vel, luctus
                  pulvinar, hendrerit id, lorem. Maecenas nec odio et ante
                  tincidunt tempus. Donec vitae sapien ut libero venenatis
                  faucibus. Nullam quis ante. Etiam sit amet orci eget eros
                  faucibus tincidunt. Duis leo. Sed fringilla mauris sit
                  amet nibh. Donec sodales sagittis magna. Sed consequat,
                  leo eget bibendum sodales, augue velit cursus nunc,
                  quis gravida magna misa libero. Fusce vulputate eleifend
                  sapien. Vestibulum purus quam, scelerisque ut, mollis
                  sed, nonummy id, metus. Nullam accumsan lorem in dui. Cras
                  ultricies mi eu turpis hendrerit fringilla. Vestibulum ante
                  ipsum primis in faucibus orci luctus et ultrices posuere
                  cubilia Curae; In ac dui quis mi consectetuer lacinia.
               </p>
                  <p class="sub_detail">sub&ndash;detail1</p>
                  <p class="sub_detail">sub&ndash;detail2</p>
                  <p class="sub_detail">sub&ndash;detail3</p>
            </div>
            <h2 id="detail3">Detail3</h2>
            <div class="detail_wrapper">
               <p class="detail">
                  Nam pretium turpis et arcu. Duis arcu tortor, suscipit
                  eget, imperdiet nec, imperdiet iaculis, ipsum. Sed
                  aliquam ultrices mauris. Integer ante arcu, accumsan a,
                  consectetuer eget, posuere ut, mauris. Praesent adipiscing.
                  Phasellus ullamcorper ipsum rutrum nunc. Nunc nonummy
                  metus. Vestibulum volutpat pretium libero. Cras id
                  dui. Aenean ut eros et nisl sagittis vestibulum. Nullam nulla
                  eros, ultricies sit amet, nonummy id, imperdiet feugiat,
                  pede. Sed lectus. Donec mollis hendrerit risus. Phasellus
                  nec sem in justo pellentesque facilisis. Etiam imperdiet
                  imperdiet orci. Nunc nec neque. Phasellus leo dolor,
                  tempus non, auctor et, hendrerit quis, nisi.
               </p>
                  <p class="sub_detail">sub&ndash;detail1</p>
                  <p class="sub_detail">sub&ndash;detail2</p>
                  <p class="sub_detail">sub&ndash;detail3</p>
            </div>
            <h2 id="detail4">Detail4</h2>
            <div class="detail_wrapper">
               <p class="detail">
                  Curabitur ligula sapien, tincidunt non, euismod vitae,
                  posuere imperdiet, leo. Maecenas malesuada. Praesent
                  congue erat at massa. Sed cursus turpis vitae tortor. Donec
                  posuere vulputate arcu. Phasellus accumsan cursus velit.
                  Vestibulum ante ipsum primis in faucibus orci luctus et
                  ultrices posuere cubilia Curae; Sed aliquam, nisi quis
                  porttitor congue, elit erat euismod orci, ac placerat
                  dolor lectus quis orci. Phasellus consectetuer vestibulum
                  elit. Aenean tellus metus, bibendum sed, posuere ac,
                  mattis non, nunc.  Vestibulum fringilla pede sit amet
                  augue. In turpis. Pellentesque posuere.  Praesent turpis.
               </p>
                  <p class="sub_detail">sub&ndash;detail1</p>
                  <p class="sub_detail">sub&ndash;detail2</p>
                  <p class="sub_detail">sub&ndash;detail3</p>
            </div>
            <h2 id="detail5">Detail5</h2>
            <div class="detail_wrapper">
               <p class="detail">
                  Aenean posuere, tortor sed cursus feugiat, nunc augue blandit
                  nunc, eu sollicitudin urna dolor sagittis lacus. Donec
                  elit libero, sodales nec, volutpat a, suscipit non,
                  turpis. Nullam sagittis. Suspendisse pulvinar, augue
                  ac venenatis condimentum, sem libero volutpat nibh, nec
                  pellentesque velit pede quis nunc. Vestibulum ante ipsum
                  primis in faucibus orci luctus et ultrices posuere cubilia
                  Curae; Fusce id purus. Ut varius tincidunt libero. Phasellus
                  dolor. Maecenas vestibulum mollis diam. Pellentesque ut
                  neque. Pellentesque habitant morbi tristique senectus et
                  netus et malesuada fames ac turpis egestas.
               </p>
                  <p class="sub_detail">sub&ndash;detail1</p>
                  <p class="sub_detail">sub&ndash;detail2</p>
                  <p class="sub_detail">sub&ndash;detail3</p>
            </div>
            <h2 id="detail6">Detail6</h2>
            <div class="detail_wrapper">
               <p class="detail">
                  In dui magna, posuere eget, vestibulum et, tempor
                  auctor, justo. In ac felis quis tortor malesuada
                  pretium. Pellentesque auctor neque nec urna. Proin sapien
                  ipsum, porta a, auctor quis, euismod ut, mi. Aenean viverra
                  rhoncus pede. Pellentesque habitant morbi tristique senectus
                  et netus et malesuada fames ac turpis egestas. Ut non enim
                  eleifend felis pretium feugiat. Vivamus quis mi. Phasellus
                  a est. Phasellus magna.
               </p>
                  <p class="sub_detail">sub&ndash;detail1</p>
                  <p class="sub_detail">sub&ndash;detail2</p>
                  <p class="sub_detail">sub&ndash;detail3</p>
            </div>
            <h2 id="detail7">Detail7</h2>
            <div class="detail_wrapper">
               <p class="detail">
                  In hac habitasse platea dictumst. Curabitur at lacus ac
                  velit ornare lobortis. Curabitur a felis in nunc fringilla
                  tristique. Morbi mattis ullamcorper velit. Phasellus
                  gravida semper nisi. Nullam vel sem.  Pellentesque libero
                  tortor, tincidunt et, tincidunt eget, semper nec, quam.
                  Sed hendrerit. Morbi ac felis. Nunc egestas, augue at
                  pellentesque laoreet, felis eros vehicula leo, at malesuada
                  velit leo quis pede. Donec interdum, metus et hendrerit
                  aliquet, dolor diam sagittis ligula, eget egestas libero
                  turpis vel mi. Nunc nulla. Fusce risus nisl, viverra et,
                  tempor et, pretium in, sapien. Donec venenatis vulputate
                  lorem.
               </p>
                  <p class="sub_detail">sub&ndash;detail1</p>
                  <p class="sub_detail">sub&ndash;detail2</p>
                  <p class="sub_detail">sub&ndash;detail3</p>
            </div>
         </div> <!-- End of main_content container -->

         <div id="side_menu">
            <div class="menu_wrapper">
               <p class="side_nav">
                  <a href="#detail1">Detail1</a>
               </p>
               <p class="side_nav">
                  <a href="#detail2">Detail2</a>
               </p>
               <p class="side_nav">
                  <a href="#detail3">Detail3</a>
               </p>
               <p class="side_nav">
                  <a href="#detail4">Detail4</a>
               </p>
               <p class="side_nav">
                  <a href="#detail5">Detail5</a>
               </p>
               <p class="side_nav">
                  <a href="#detail6">Detail6</a>
               </p>
               <p class="side_nav">
                  <a href="#detail7">Detail7</a>
               </p>
            </div> <!-- End of menu_wrapper container -->
         </div> <!-- End of side_menu container -->

         <div id="page_foot">
            <strong>Page Footer</strong>
         </div> <!-- End of page_foot container -->
      </div> <!-- End of wrapper container -->
   </body>
</html>
```

---

### Post by DaveNelson on 2014-08-10
I did find one trick to get the first detail to jump to the position where I want it. First of all I had margin-top defined twice at 10.5 and 10 em. I removed those two lines and inserted a 700x100 pixel transparent image above detail1 in the HTML, and styled it to be 70 em wide by 100 em tall, so that it remains proportionate when the browser's display is zoomed. By giving the image id="detail1", that link works as I would like, appearance-wise. Not sure if that is the best or only solution though.

Obviously I can id other elements in such a way as to get the other details to appear where I want them, but if anything changes between that element and the detail heading then I will have re-calculate the id's position. So it seems to me a more elegant solution may be possible.

Since I have not gotten any replies in a day, should I assume that I may not have picked the best place to post my question? If that is the case then I am open to other site suggestions. I started here because I am doing my design work on a Ubuntu box, even though our server runs Red Hat. Mind you, I'm not complaining since this could be an esoteric enough of a question that help may not be readily available. Of course it could also be that the answer is so obvious that everyone is shaking their head at my naivety.

Regards,
Dave

---

### Post by Dimarchi on 2014-08-11
You have indeed picked the best place to post your question (here). I  noticed this thread yesterday just before going to sleep, so don't be so  hasty in expecting an answer. :) I have been dabbling now and then in a  somewhat similar situation just to see in how many ways I can twist the  appearance of the same document structure (except menu links taking the  place of page_header), which is why I'm interested in this, as well. I  never considered anchors to pose a problem, but it looks like they can.  The answer is not that obvious, in my opinion.

As a quick and  dirty way I don't see other way than scripting (I'm hesitant to mess  with document structure by adding stuff that doesn't *need* to be there,  but that is just personal view...what works for you works for you). I  have saved the code you have provided to mess with it. I might not  figure it out, so there will be no reply. There are other knowledgeable  people here, though, who may take interest in this challenge.

---

### Post by DaveNelson on 2014-08-11
Thanks Dimarchi, for setting me straight. I was trying not to appear too hasty. Having been around since dial-up BBS I seem to have forgotten what is was like to have to wait days for activity.

I will check back occasionally, and obviously I will post any solution I find. But I won't have too much time to work on this before Wednesday anyhow (I'm GMT -5).

Be aware that in my CSS I have magin-top defined twice. This:
```
#main_content,
#side_menu
{
   float:                    left;
   margin-top:               10.5em;
   min-height:               35em;
}

#main_content
{
   margin-bottom:            1em;
   margin-left:              20em;
   margin-top:               10em;
   width:                    67.5em;
}
```

should be:
```
#main_content,
#side_menu
{
   float:                    left;
   margin-top:               10.5em;
   min-height:               35em;
}

#main_content
{
   margin-bottom:            1em;
   margin-left:              20em;
/*   margin-top:               10em; */
   width:                    67.5em;
}
```

Scripting was definitely in the back of my mind, but that won't help the users that do not have, or use Javascript. I would like to accommodate them as well, if possible, especially since I tend to be one of them myself.

Regards,
Dave

---

### Post by Dimarchi on 2014-08-12
I have made the fix you mentioned, and as per your wish, I am now trying to achieve this without scripting. So far, I have removed wrapper entirely, as well as background gradient image (using CSS gradient in place, probably not in the manner you intended) and inlined CSS to the HTML document - that is, CSS and HTML are both in the same file just for this. Result: I have sorta kinda...working...result. Not pretty, but it works in all the browsers I have tested exactly the same way: Firefox (Windows and Linux), Chrome/Chromium (Windows/Linux), Opera (Windows), Internet Explorer (version 11, Windows).

Not pretty means there is a page_header size of space above each detailx. Whether that is good or bad I'll leave up to you. :) I'll keep working on this, though.

---

### Post by Dimarchi on 2014-08-13
The code I mentioned above for your perusal.

```
<!DOCTYPE html>
<html lang="en">
   <head>
      <meta name="Author" content="D. Nelson" >
      <meta charset="UTF-8">
      <meta name="description" content="testing boxes" >
      <title>
         box layout test
      </title>
<style type="text/css">
*
{
   margin:                   0;
   padding:                  0;
}

html
{
   color:                    #000000;
   font-size:                100%;
    background: rgba(73,155,234,0);
    background: -moz-linear-gradient(top, rgba(73,155,234,0) 0%, rgba(0,76,158,1) 100%);
    background: -webkit-gradient(left top, left bottom, color-stop(0%, rgba(73,155,234,0)), color-stop(100%, rgba(0,76,158,1)));
    background: -webkit-linear-gradient(top, rgba(73,155,234,0) 0%, rgba(0,76,158,1) 100%);
    background: -o-linear-gradient(top, rgba(73,155,234,0) 0%, rgba(0,76,158,1) 100%);
    background: -ms-linear-gradient(top, rgba(73,155,234,0) 0%, rgba(0,76,158,1) 100%);
    background: linear-gradient(to bottom, rgba(73,155,234,0) 0%, rgba(0,76,158,1) 100%);
    filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#499bea', endColorstr='#004c9e', GradientType=0 );
}

body
{
   background-color:         white;
   font-family:              "Times Roman", serif;
   font-size:                62.5%;

   margin-left:              auto;
   margin-right:             auto;
   min-height:               45em;
   width:                    90em;
}

.detail
{
   font-size:                1.5em;
   font-style:               normal;
}

.detail_wrapper
{
   margin-bottom:            1em;
   margin-left:              2.7em;
}

.menu_wrapper
{
   margin-left:              1em;
   width:                    18em;
}

.side_nav
{
   font-size:                1.25em;
}

.sub_detail
{
   padding-left:             2em;
   font-size:                1.5em;
}

#main_content,
#side_menu
{
   float:                    left;
   margin-top:               10.5em;
   min-height:               35em;
}

#main_content
{
   margin-bottom:            1em;
   margin-left:              20em;
   width:                    67.5em;
}

#main_content h1
{
   border-bottom-color:      #000000;
   border-bottom-style:      solid;
   border-bottom-width:      0.05em;
   font-size:                3em;
   padding-bottom:           0.10em;
}

#main_content h2
{
   font-size:                2.5em;
}

#main_content h3
{
   font-size:                2em;
   margin-left:              -1.3em;
}

#page_foot
{
   border-top-color:         #000000;
   border-top-style:         solid;
   border-top-width:         0.1em;
   clear:                    both;
   font-size:                2em;
   padding-top:              1em;
   text-align:               center;
}

#page_head
{
   background-color:         #FFFFFF;
   background-image:         url(./fadedown.png);
   border-bottom-color:      #000000;
   border-bottom-style:      solid;
   border-bottom-width:      0.2em;
   height:                   10em;
   margin-bottom:            0.1em;
   position:                 fixed;
   text-align:               center;
   width:                    90em;
}

#page_head h1
{
   font-size:                5em;
}

#page_head h2
{
   font-size:                2.5em;
}

#side_menu
{
   position:                 fixed;
   width:                    20em;
}

h2[id^=detail] {
    padding-top: calc(55% - 10.5em);
}
</style>
   </head>
   <body>
         <div id="page_head">
            <h2>Sub&ndash;Title</h2>
            <h1>Main Title</h1>
         </div> <!-- End of the page_head container -->

         <div id="main_content">
            <h1>Content Title </h1>
            <h2 id="detail1">Detail1</h2>
            <div class="detail_wrapper">
               <p class="detail">
                  Lorem ipsum dolor sit amet, consectetuer adipiscing
                  elit. Aenean commodo ligula eget dolor. Aenean massa. Cum
                  sociis natoque penatibus et magnis dis parturient montes,
                  nascetur ridiculus mus. Donec quam felis, ultricies nec,
                  pellentesque eu, pretium quis, sem. Nulla consequat massa
                  quis enim.  Donec pede justo, fringilla vel, aliquet nec,
                  vulputate eget, arcu. In enim justo, rhoncus ut, imperdiet a,
                  venenatis vitae, justo. Nullam dictum felis eu pede mollis
                  pretium. Integer tincidunt. Cras dapibus. Vivamus elementum
                  semper nisi. Aenean vulputate eleifend tellus. Aenean
                  leo ligula, porttitor eu, consequat vitae, eleifend
                  ac, enim. Aliquam lorem ante, dapibus in, viverra quis,
                  feugiat a, tellus. Phasellus viverra nulla ut metus varius
                  laoreet. Quisque rutrum. Aenean imperdiet. Etiam ultricies
                  nisi vel augue. Curabitur ullamcorper ultricies nisi. Nam
                  eget dui.
               </p>
                  <p class="sub_detail">sub&ndash;detail1</p>
                  <p class="sub_detail">sub&ndash;detail2</p>
                  <p class="sub_detail">sub&ndash;detail3</p>
            </div>
            <h2 id="detail2">Detail2</h2>
            <div class="detail_wrapper">
               <p class="detail">
                  Etiam rhoncus. Maecenas tempus, tellus eget condimentum
                  rhoncus, sem quam semper libero, sit amet adipiscing
                  sem neque sed ipsum. Nam quam nunc, blandit vel, luctus
                  pulvinar, hendrerit id, lorem. Maecenas nec odio et ante
                  tincidunt tempus. Donec vitae sapien ut libero venenatis
                  faucibus. Nullam quis ante. Etiam sit amet orci eget eros
                  faucibus tincidunt. Duis leo. Sed fringilla mauris sit
                  amet nibh. Donec sodales sagittis magna. Sed consequat,
                  leo eget bibendum sodales, augue velit cursus nunc,
                  quis gravida magna misa libero. Fusce vulputate eleifend
                  sapien. Vestibulum purus quam, scelerisque ut, mollis
                  sed, nonummy id, metus. Nullam accumsan lorem in dui. Cras
                  ultricies mi eu turpis hendrerit fringilla. Vestibulum ante
                  ipsum primis in faucibus orci luctus et ultrices posuere
                  cubilia Curae; In ac dui quis mi consectetuer lacinia.
               </p>
                  <p class="sub_detail">sub&ndash;detail1</p>
                  <p class="sub_detail">sub&ndash;detail2</p>
                  <p class="sub_detail">sub&ndash;detail3</p>
            </div>
            <h2 id="detail3">Detail3</h2>
            <div class="detail_wrapper">
               <p class="detail">
                  Nam pretium turpis et arcu. Duis arcu tortor, suscipit
                  eget, imperdiet nec, imperdiet iaculis, ipsum. Sed
                  aliquam ultrices mauris. Integer ante arcu, accumsan a,
                  consectetuer eget, posuere ut, mauris. Praesent adipiscing.
                  Phasellus ullamcorper ipsum rutrum nunc. Nunc nonummy
                  metus. Vestibulum volutpat pretium libero. Cras id
                  dui. Aenean ut eros et nisl sagittis vestibulum. Nullam nulla
                  eros, ultricies sit amet, nonummy id, imperdiet feugiat,
                  pede. Sed lectus. Donec mollis hendrerit risus. Phasellus
                  nec sem in justo pellentesque facilisis. Etiam imperdiet
                  imperdiet orci. Nunc nec neque. Phasellus leo dolor,
                  tempus non, auctor et, hendrerit quis, nisi.
               </p>
                  <p class="sub_detail">sub&ndash;detail1</p>
                  <p class="sub_detail">sub&ndash;detail2</p>
                  <p class="sub_detail">sub&ndash;detail3</p>
            </div>
            <h2 id="detail4">Detail4</h2>
            <div class="detail_wrapper">
               <p class="detail">
                  Curabitur ligula sapien, tincidunt non, euismod vitae,
                  posuere imperdiet, leo. Maecenas malesuada. Praesent
                  congue erat at massa. Sed cursus turpis vitae tortor. Donec
                  posuere vulputate arcu. Phasellus accumsan cursus velit.
                  Vestibulum ante ipsum primis in faucibus orci luctus et
                  ultrices posuere cubilia Curae; Sed aliquam, nisi quis
                  porttitor congue, elit erat euismod orci, ac placerat
                  dolor lectus quis orci. Phasellus consectetuer vestibulum
                  elit. Aenean tellus metus, bibendum sed, posuere ac,
                  mattis non, nunc.  Vestibulum fringilla pede sit amet
                  augue. In turpis. Pellentesque posuere.  Praesent turpis.
               </p>
                  <p class="sub_detail">sub&ndash;detail1</p>
                  <p class="sub_detail">sub&ndash;detail2</p>
                  <p class="sub_detail">sub&ndash;detail3</p>
            </div>
            <h2 id="detail5">Detail5</h2>
            <div class="detail_wrapper">
               <p class="detail">
                  Aenean posuere, tortor sed cursus feugiat, nunc augue blandit
                  nunc, eu sollicitudin urna dolor sagittis lacus. Donec
                  elit libero, sodales nec, volutpat a, suscipit non,
                  turpis. Nullam sagittis. Suspendisse pulvinar, augue
                  ac venenatis condimentum, sem libero volutpat nibh, nec
                  pellentesque velit pede quis nunc. Vestibulum ante ipsum
                  primis in faucibus orci luctus et ultrices posuere cubilia
                  Curae; Fusce id purus. Ut varius tincidunt libero. Phasellus
                  dolor. Maecenas vestibulum mollis diam. Pellentesque ut
                  neque. Pellentesque habitant morbi tristique senectus et
                  netus et malesuada fames ac turpis egestas.
               </p>
                  <p class="sub_detail">sub&ndash;detail1</p>
                  <p class="sub_detail">sub&ndash;detail2</p>
                  <p class="sub_detail">sub&ndash;detail3</p>
            </div>
            <h2 id="detail6">Detail6</h2>
            <div class="detail_wrapper">
               <p class="detail">
                  In dui magna, posuere eget, vestibulum et, tempor
                  auctor, justo. In ac felis quis tortor malesuada
                  pretium. Pellentesque auctor neque nec urna. Proin sapien
                  ipsum, porta a, auctor quis, euismod ut, mi. Aenean viverra
                  rhoncus pede. Pellentesque habitant morbi tristique senectus
                  et netus et malesuada fames ac turpis egestas. Ut non enim
                  eleifend felis pretium feugiat. Vivamus quis mi. Phasellus
                  a est. Phasellus magna.
               </p>
                  <p class="sub_detail">sub&ndash;detail1</p>
                  <p class="sub_detail">sub&ndash;detail2</p>
                  <p class="sub_detail">sub&ndash;detail3</p>
            </div>
            <h2 id="detail7">Detail7</h2>
            <div class="detail_wrapper">
               <p class="detail">
                  In hac habitasse platea dictumst. Curabitur at lacus ac
                  velit ornare lobortis. Curabitur a felis in nunc fringilla
                  tristique. Morbi mattis ullamcorper velit. Phasellus
                  gravida semper nisi. Nullam vel sem.  Pellentesque libero
                  tortor, tincidunt et, tincidunt eget, semper nec, quam.
                  Sed hendrerit. Morbi ac felis. Nunc egestas, augue at
                  pellentesque laoreet, felis eros vehicula leo, at malesuada
                  velit leo quis pede. Donec interdum, metus et hendrerit
                  aliquet, dolor diam sagittis ligula, eget egestas libero
                  turpis vel mi. Nunc nulla. Fusce risus nisl, viverra et,
                  tempor et, pretium in, sapien. Donec venenatis vulputate
                  lorem.
               </p>
                  <p class="sub_detail">sub&ndash;detail1</p>
                  <p class="sub_detail">sub&ndash;detail2</p>
                  <p class="sub_detail">sub&ndash;detail3</p>
            </div>
         </div> <!-- End of main_content container -->

         <div id="side_menu">
            <div class="menu_wrapper">
               <p class="side_nav">
                  <a href="#detail1">Detail1</a>
               </p>
               <p class="side_nav">
                  <a href="#detail2">Detail2</a>
               </p>
               <p class="side_nav">
                  <a href="#detail3">Detail3</a>
               </p>
               <p class="side_nav">
                  <a href="#detail4">Detail4</a>
               </p>
               <p class="side_nav">
                  <a href="#detail5">Detail5</a>
               </p>
               <p class="side_nav">
                  <a href="#detail6">Detail6</a>
               </p>
               <p class="side_nav">
                  <a href="#detail7">Detail7</a>
               </p>
            </div> <!-- End of menu_wrapper container -->
         </div> <!-- End of side_menu container -->

         <div id="page_foot">
            <strong>Page Footer</strong>
         </div> <!-- End of page_foot container -->
   </body>
</html>
```

---

### Post by DaveNelson on 2014-08-18
Thanks Dimarchi,

I've not had a chance to get back to this, thanks to my "real" job. But it looks very usable. I will let you know. And thank you for the gradient hints. I had looked at that but wasn't exactly clear on the concept, so you've given me another example to work with.

I will be traveling this week, so apologies in advance if you don't hear back from me for a few days.

Dave

---

