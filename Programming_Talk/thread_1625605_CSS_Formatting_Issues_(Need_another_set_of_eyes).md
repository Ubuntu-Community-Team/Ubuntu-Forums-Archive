---
title: "CSS Formatting Issues (Need another set of eyes)"
date: 2010-11-19
forum: Programming Talk
---

### Post by dhtseany on 2010-11-19
Hey everybody, and thanks in advance for any help ;)

I'm working on a website for a client which has a lot of PHP driven forms for the general public to submit insurance quotes to said customer. Everything is going well except for one CSS related issue. What I want to accomplish is the ability to designate an <input> field to be a "money field". The basic goal is whatever fields I specify as money will be as follows in the HTML:
```
<input type='text' class='money' />
```

The idea is that when I specify that class, it should:
1. Display a PNG background image of a dollar sign on the left with a 20px padding-left so the cursor and text won't overlap the PNG image.
2. Otherwise hold the same formatting as the rest of the inputs that are not using the "money" class. 

The initial issue I had was the padding-left @ 20px was expanding the input fields designated as a money field 20px wider than the normal, non money related fields.

I fixed this by using the following CSS:
```

input {         <--This
  width:140px;  <--This
}               <--This

input,
textarea,
select {
  padding: 1px;
  font: 400 1em verdana, sans-serif;
  color: #999;
  background: #EEE;
  border: 1px solid #CCC;
}
input.money {
  width: 120px; <--This
  padding: 1px;
  font: 400 1em verdana, sans-serif;
  color: #999;
  background: #EEE;
  background-image:url(../images/dollar-sign.png);
  background-repeat:no-repeat;
  padding-left: 20px;  <--This
  border: 1px solid #CCC;
}

input:focus,
input:hover,
textarea:focus,
textarea:hover,
select:focus,
select:hover {
  color: #000;
  background: #E7F1F3;
  border: 1px solid #888;
}

input.money:focus,
input.money:hover{
  color: #000;
  background-image:url(../images/dollar-sign.png);
  background-repeat:no-repeat;
  border: 1px solid #888;
}

```

It's also noteworthy to post this chunk from the layout.css style sheet, however none of the width classes are in use with the affected form objects.

```

/* Custom Table Width Fix */
.autowidth {
	width:auto;
}

/* Column widths */
.width {
  width: 776px;
}

.widthPad {
  width: 746px;
}

.width10 {
  width: 20%;
}

.width25 {
  width: 24%;
}

.width50 {
  width: 48%;
}

.width73 {
  width: 73%;
}

.width75 {
  width: 75%;
}

.width100 {
  width: 100%;
}

```

This was a free, premade layout so I'm trying to adapt the existing code to meet my needs without totally messing up the original layout formatting.

**This is the best example of the extra gaps that suddenly appeared**
[IMG]http://img404.imageshack.us/img404/1365/css1.png[/IMG]

**Another spot where the same issues are occuring**
[IMG]http://img148.imageshack.us/img148/7775/css2r.png[/IMG]

**This is what I'm shooting for**
[IMG]http://img139.imageshack.us/img139/2604/css3.png[/IMG]

The first thing is that this code just seems "bloated" and that's not how I do things. However and beyond that, what's happening now is every checkbox and radio button seem to suddenly be affected by my "fix". I should also point out the issue seems to be browser independent as both IE8 and FF3.6.12 display the same, incorrect spacing.

First, did I choose the best method for the PNG/dollar sign goal? Second, why would the preceding code affect the other form elements?

Thanks again for any help you guys can offer.

Peace
Sean

---

### Post by Colonel Kilkenny on 2010-11-19
Bit difficult to say when there's no test case to mess with (even a small html page with form and those css would be fine).

Anyway, you're saying in CSS that inputs should be 140px wide. And the current CSS affects every single input element (including checkboxes, radio buttons, etc.).
So, you need to make sure that only textfields have width of 140px. There's many ways to do that.
First that comes to mind is to simply use attribute selector:
[PHP]
input[type="text"] {
width: 140px;
}
[/PHP]
That would apply the width of 140px only for input elements which are textfields (i.e. they have attribute type with value "text"). But remember that older browsers don't support attribute selectors (can't really remember when the support came to IE for an example)...

Another way that comes to mind would be to add in html all textfields new class. Let's say 'thisisatextfield'. And then just
[PHP]
input.thisisatextfield {
width: 140px;
}
[/PHP]
instead of the current rule.

---

### Post by dhtseany on 2010-11-19
Hi, and thanks for the response!

First, I've made a quick mockup of the site using one of the original template pages with my current CSS style sheets. There are 3 files: html.css, layout.css, and test.htm.

Second, wasn't your second suggestion basically what I already did by creating the input.money{ class? If not, maybe I'm not seeing the difference :P

Thanks again!

Peace
Sean

**test.htm**
```

<!DOCTYPE html PUBLIC '-//W3C//DTD XHTML 1.0 Strict//EN'
    'http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd'>

<html xmlns='http://www.w3.org/1999/xhtml' xml:lang='en' lang='en'>

<head>


  <title>Contact Us</title>
  <meta http-equiv='content-type' content='application/xhtml+xml; charset=UTF-8' />
  
  <link rel='stylesheet' type='text/css' href='css/layout.css' media='screen, projection, tv ' />
  <link rel='stylesheet' type='text/css' href='css/html.css' media='screen, projection, tv ' />

 
</head>

<body>

<!-- #content: holds all except site footer - causes footer to stick to bottom -->
<div id='content'>

  <!-- #header: holds the logo and top links -->
  <div id='header' class='width'>
&nbsp;

    <ul>
      <li><a href='index.php'>Back to Main page</a></li>

    </ul>

  </div>
  <!-- #header end -->


  <!-- #headerImg: holds the main header image or flash -->
  <div id='headerImg' class='width'></div>




  <!-- #menu: the main large box site menu -->
  <div id='menu' class='width'>
    <ul>
      <li>
        <a href='start.php' onfocus='blur()'>
          <span class='title '>GET COVERED</span>
          <span class='desc'>Get started building your policy!</span>        </a>      </li>

      <li>
        <a href='faq.php' class='forum' onfocus='blur()'>
          <span class='title '>FAQ</span>
          <span class='desc style3'>Get answers to Frequently Asked Questions</span>        </a>      </li>
      <li>
        <a href='resources.php' onfocus='blur()'>
          <span class='title '>EXISTING CUSTOMERS</span>

          <span class='desc'>Online Resources for our Existing Customers</span>
        </a>
      </li>
      <li>
        <a href='contact.php' onfocus='blur()'>
          <span class='title '>CONTACT US</span>
          <span class='desc'>Find out how to contact us fast!</span>

        </a>
      </li>
    </ul>



  </div>
  <!-- #menu end -->



  <!-- #page: holds the page content -->

  <div id='page'>


    <!-- #columns: holds the columns of the page -->
    <div id='columns' class='widthPad'>


    <!-- Left column -->
    <div class='floatLeft width25 lightBlueBg horzPad'>

      <h2>Details</h2>
  

    </div>
    <!-- Left column end -->


    <!-- Right column -->
    <div class='floatRight width73'>


        <h1>Contact Us <span class='dark'>Now!</span></h1>

			<p>Use the form below to easily send us an e-mail!<br />
            <i>This form does not require a mail client such as Microsoft Outlook or Windows Mail</i>
			</p>
            <p>
			<form action='contact.php' method='POST'>
              <label>Your Name</label>
              <input type='text' name='name' />

            </p>
			<p>
              <label>Your E-mail Address</label>
              <input type='text' name='fromemail' class='money'/>
            </p>
            <p>
              <label>Your Phone Number</label>
              <input type='text' name='phone' />

            </p>

            <p>
              <label>Your Message</label>
              <textarea name='messagebody' rows='5' cols='60'></textarea>
            </p>

            <p>
              <label>Customer Status</label>

              <select name='status'>
                <option value='Existing'>Existing Customer</option>
                <option value='Prospective'>Prospective Customer</option>
              </select>
            </p>




            <p>

              <label>Preferred Contact Method</label>
              <input type='radio' name='radioGroup' value='email' class='radio'/> E-mail Me
              <input type='radio' name='radioGroup' value='call' class='radio'/> Call Me
            </p>
			<p>&nbsp;</p>
            
            <div class='lightBlueBg'>

            <h2>My Interests</h2>

            <p>
              <input type='checkbox' name='personalins' value='personalins' class='radio'/> Personal Insurance<br/>
              <input type='checkbox' name='bizins' value='bizins' class='radio'/> Business Insurance<br/>
              <input type='checkbox' name='policychanges' value='policychanges' class='radio'/> Existing Policy Changes<br/>
              <input type='checkbox' name='billing' value='billing' class='radio'/> Billing Questions<br/>

              <input type='checkbox' name='other' value='other' class='radio'/> Other <input type='text' name='othertext' 

class='width33'/>
            </p>

            </div>

 
      </form>

    </div>
    <!-- Right column end -->


    </div>
    <!-- #columns end -->

  </div>
  <!-- #page end -->

</div>
<!-- #content end -->


<!-- #footer: holds the site footer (logo and links) -->
<div id='footer'>

  <!-- #bg: applies the site width and footer background -->
  <div id='bg' class='width'>

  <!--<img src='images/logo.gif' alt='Your logo goes here'/> -->
     <ul>
      <li><a href='http://www.studio7designs.com/' target='_blank'>Design</a></li>

	</ul>

  </div>
  <!-- #bg end -->

</div>
<!-- #footer end -->

</body>

</html>

```

**layout.css**
```

/**************************************************************
   Visit FullAhead.org and studio7designs.com for more layouts and downloads for this template!
 **************************************************************/
 
/**************************************************************
   All page content except for footer
 **************************************************************/

#content {
  position: relative;
  height: auto !important;
  height: 100%;
  min-height: 100%;
}



/**************************************************************
   Topbar with newsletter form and theme change buttons
 **************************************************************/

#topbar {
  float: left;
  width: 100%;
  padding: 0.6em 0;

  font-size: 0.9em;
  text-transform: uppercase;

  color: #CFD9DB;
  background: #FFF url(../images/bg/topbar.gif) repeat-x bottom left;
}



/**************************************************************
   Top menu and logo
 **************************************************************/

#header {
	clear: both;
	position: relative;
	height: 5em;
	margin: 0 auto;
	background: #48525B url(../images/bg/header.gif) repeat-x bottom left;
	border-bottom: 2px solid #48525B;
	background-color: #48525B;
}


#header img {
  position: absolute;
  top: 5%;
  left: 10px;
}

#header ul {
  margin: 3.5em 1em 0 0 !important;
  margin: 3.5em 0.5em 0 0;
  padding: 0;
  float: right;
}

#header ul li {
  display: inline;
  list-style: none;
}

#header ul li a {
  float: left;
  padding: 0 1em;

  font: 400 1.1em arial, sans-serif;
  letter-spacing: 0.1em;
  line-height: 0.8em !important;
  line-height: 1em;

  color: #cccccc;
  border-right: 1px solid #4D5760;
}

#header ul li a.last {
  padding-right: 0;
  border-right: 0;
}

#header ul li a:hover {
  color: #3B5D77;
}



/**************************************************************
   Header Image/Flash Movie
 **************************************************************/

#headerImg {
  margin: 0 auto;
  height: 143px;
  background: url(../images/bg/callender-banner.png) no-repeat top left;
}





/**************************************************************
   Top Block Menu
 **************************************************************/

#menu {
  margin: 0 auto;
}

#menu ul {
  width: 100%;
  float: left;
  margin: 0;
  padding: 0;

  text-align: left;
  background: #3B5D77 url(../images/bg/menu.gif) repeat-x top left;
}

#menu ul li {
  display: inline;
  margin: 0;
  padding: 0;
  list-style: none;
}

#menu ul li a {
  float: left;
  width: 25%;
  height: 4.5em;

  font: 400 1.2em arial, sans-serif;
  letter-spacing: 0.1em;

  color: #fff;

  border-top: 7px solid #41637D;
  border-bottom: 15px solid #FFF;
}

#menu ul li a span {
  display: block;
  padding: 2px 7px;
}


#menu ul li a span.desc {
  font-size: 0.8em;
  color: #8C8D94;
}


#menu ul li a:hover,
#menu ul li a.here {
  background: #4A5C6A;
  border-top: 7px solid #455660;
}

#menu ul li a:hover span.desc,
#menu ul li a.here span.desc {
  color: #FFF;
}


/* Top menu icons */
#menu ul li a span.speaker {
  padding-left: 22px;
  background: url(../images/icons/speaker.gif) no-repeat 5px 50%;
}

#menu ul li a:hover span.speaker {
  background: url(../images/icons/speaker_on.gif) no-repeat 5px 50%;
}

#menu ul li a span.bubble {
  padding-left: 24px;
  background: url(../images/icons/bubble.gif) no-repeat 4px 4px;
}

#menu ul li a:hover span.bubble {
  background: url(../images/icons/bubble_on.gif) no-repeat 4px 4px;
}

#menu ul li a span.heart {
  padding-left: 20px;
  background: url(../images/icons/heart.gif) no-repeat 3px 50%;
}

#menu ul li a:hover span.heart {
  background: url(../images/icons/heart_on.gif) no-repeat 3px 50%;
}


#menu ul li a span.dollar {
  padding-left: 20px;
  background: url(../images/icons/dollar.gif) no-repeat 4px 50%;
}

#menu ul li a:hover span.dollar {
  background: url(../images/icons/dollar_on.gif) no-repeat 4px 50%;
}




/**************************************************************
   Page Content
 **************************************************************/

#page {
  clear: both;
  float: left;
  width: 100%;
  margin-bottom: 6em;
  text-align: left;
}

#columns {
  margin: 0 auto;
}

/* Custom Table Width Fix */
.autowidth {
	width:auto;
}

/* Column widths */
.width {
  width: 776px;
}

.widthPad {
  width: 746px;
}

.width10 {
  width: 20%;
}

.width25 {
  width: 24%;
}

.width50 {
  width: 48%;
}

.width73 {
  width: 73%;
}

.width75 {
  width: 75%;
}

.width100 {
  width: 100%;
}


/**************************************************************
   Footer
 **************************************************************/


#footer {
  clear: both;
  float: left;
  width: 100%;
  height: 5em;
  margin-top: -5em;
}

#footer #bg {
  position: relative;
  height: 5em;
  margin: 0 auto;
  background: #49525B url(../images/bg/header.gif) repeat-x bottom left;
}

#footer #bg ul {
  float: right;
  margin: 3em 1em 0 0 !important;
  margin: 3em 0.5em 0 0;
  padding: 0;
}

#footer #bg ul li {
  display: inline;
  list-style: none;
}

#footer #bg ul li a {
  float: left;
  padding: 0 1em;

  font: 400 1em arial, sans-serif;
  letter-spacing: 0.1em;
  line-height: 0.8em !important;
  line-height: 1em;

  color: #4D5760;
  border-right: 1px solid #4D5760;
}

#footer #bg ul li a.last {
  padding-right: 0;
  border-right: 0;
}

#footer #bg ul li a:hover {
  color: #6C0;
}

#footer #bg img {
  position: absolute;
  top: 6%;
  left: 10px;
}



/**************************************************************
   Icons specific to the colour theme
 **************************************************************/

a.lightTheme img,
a.darkTheme img,
a.submitButton img {
  width: 20px;
  height: 20px;
  vertical-align: middle;
}

a.lightTheme img {
  background: url(../images/icons/light_light_theme.gif) no-repeat center center;
}

a.darkTheme img {
  background: url(../images/icons/light_dark_theme.gif) no-repeat center center;
}

a.submitButton img {
  background: url(../images/icons/light_submit.gif) no-repeat center center;
}


/**************************************************************
   Posts
 **************************************************************/

.post {
  float: left;
  width: 100% !important;
  width: 99%;
  position: relative;

  margin-bottom: 1.5em;

  border-bottom: 1px solid #CCCCCC;
}

.post .date {
  position: absolute;
  top: 0;
  left: 5px;

  width: 2.3em;
  text-align: right;
}

.post .date .month {
  text-transform: uppercase;
  font: 700 1.0em arial, sans-serif;
  color: #888;
}

.post .date .day {
  display: block;
  margin-top: -5px;
  font: 700 2.1em arial, sans-serif;
  color: #888;
}

.post .title {
  display: block;
  padding: 0 0 5px 0;

  font-size: 1.2em;
  font-weight: bold;
  color: #586B7A;
}

.post p {
  margin: 0 0 0 3.5em;
  padding:  0 0 1em 1.2em;
  border-left: 1px solid #CCCCCC;
}



/**************************************************************
   Thumbnail Lists
 **************************************************************/

ul.thumbs,
ul.thumbs li {
  margin: 0;
  padding: 0;
}

ul.thumbs li {
  margin: 0 0 15px 0 !important;
  margin: 0;
  padding: 0px;
  list-style: none;
}

a.thumb img {
  
  border: 5px solid #ccc;
}

a:hover.thumb img {
  background: #8EB4C6;
  border: 5px solid #668FA3;
}

a:hover.thumb {
  background: none;
}

a.thumb span {
  display: block;
  margin-top: -5px !important;
  margin-top: -2px;
}



/**************************************************************
   Submenu Styles
 **************************************************************/

ul.submenu1,
ul.submenu2 {
  margin: 0 0 20px 0;
  padding: 0;
}

ul.submenu1 li,
ul.submenu2 li{
  margin: 0;
  padding: 0;
  list-style: none;
  list-style-image: url(foo.gif); /* because IE is balls */
}

ul.submenu1 li a,
ul.submenu2 li a {
  display: block;
  height: auto !important;

  /* Start hide from IE Mac \*/
  height: 1%;
  /* End hide from IE Mac */

  padding: 1px 5px 1px 20px;
}

ul.submenu1 li a {
  background: url(../images/bg/submenu1.gif) no-repeat 5px 50%;
}

ul.submenu1 a:hover {
  color: #426F85;
  background: #B3C6C4 url(../images/bg/submenu1.gif) no-repeat 5px 50%;
}

ul.submenu2 li a {
  color: #426F85;
  background: url(../images/bg/submenu2.gif) no-repeat 3px 50%;
}

ul.submenu2 a:hover {
  color: #426F85;
  background: #B3C6C4 url(../images/bg/submenu2.gif) no-repeat 3px 50%;
}






/**************************************************************
   Generic Display 
 **************************************************************/


.block {
  display: block;
}

.clear {
  clear: both;
}

.marginRight {
  margin-right: 15px;
}

.paddingLeft {
  padding-left: 5px;
}

.paddingRight {
  padding-right: 5px;
}

.floatLeft {
  float: left;
}

.floatRight {
  float: right;
}

.alignLeft {
  text-align: left;
}

.alignRight {
  text-align: right;
}

.alignTop {
  vertical-align: top;
}

.alignMiddle {
  vertical-align: middle;
}

.alignBottom {
  vertical-align: bottom;
}

.lightBlueBg {
  background-color: #EAF2F5;
}

.dark {
  color: #353E47;
}

.moneyright {
	position:relative;
	top: 0px;
	right: 20px;
}

```

**html.css**
```

/**************************************************************
   Visit FullAhead.org and studio7designs.com for more layouts and downloads for this template!
 **************************************************************/

/*********************************************************
   HTML Elements
 *********************************************************/

html,
body {
  height: 100%;
}

body {
  margin: 0;
  padding: 0;
  text-align: center;
  background: url(../images/bg/light_body.gif) repeat-y top center;
  font: 400 0.7em verdana, arial, sans-serif;
  color: #555;
}


/* Headers */
h1, h2, h3, h4, h5 {
  margin: 0 0 10px 0;
  padding: 0;
}

h6 {
  margin-bottom: 0.5em;
  padding: 0;
  text-transform:uppercase;
  color:#09F;
  font-size:14px;
}

h7 {
  margin-bottom: 0.5em;
  padding: 0;
  text-transform:uppercase;
  color:#999;
  font-size:14px;
}
	
h1 {
  padding-bottom: 0.2em;

  font: 400 1.6em arial, sans-serif;
  color: #536C71;
  border-bottom: 12px solid #ddd;
}

h2 {
  font-size: 1.2em;
  color: #586B7A;
}

h3 {
  text-transform: uppercase;
  font-size: 0.9em;
  color: #5D6F73;
}

h4 {
  font-size: 0.85em;
}

h5 {
  font-size: 0.8em;
}


/* Needed to horizontally pad in a coloured container */
.horzPad h1,
.horzPad h2,
.horzPad h3,
.horzPad h4,
.horzPad h5,
.horzPad p {
  padding-left: 5px;
  padding-right: 5px;
}


/* Links */
a {
  text-decoration: none;
  color: #3B5D77;
}

a:hover {
  color: #668FA3;
}

a img {
  border: 0;
}

a img.border {  
  border: 1px solid #FC3307;
}

a:hover img.border {  
  /* Fixes IE bug - IE doesn't correctly apply the style on a:hover so need to mask it */
  border: 1px solid #668FA3 !important;
  border: 1px solid #FC3307;
}



/* Images */
img.floatRight {
  margin: 5px 0 10px 10px;
}

img.floatLeft {
  margin: 5px 10px 10px 0;
}



/* Lists */
ul li {
  list-style-image: url(../images/bg/submenu1.gif);
}

ol li {
  font-weight: bold;
  color: #668FA3;
}

ol li span {
  font-weight: normal;
  color: #444;
}


/* Blockquote */
blockquote {
  margin: 0;
  padding: 0 20px;
  background: #E7F1F3;
  border-top: 1px solid #AAD3DB;
  border-bottom: 1px solid #AAD3DB;
}



/**************************************************************
   Form Elements
 **************************************************************/

form {
  padding: 0;
  margin: 0;
}

/* If you're finding the input elements get pushed down, increase the width */
label {
  float: left;
  width: 25%;
  vertical-align: top;
}
input {
	width:140px;
}

input,
textarea,
select {
  padding: 1px;
  font: 400 1em verdana, sans-serif;
  color: #999;
  background: #EEE;
  border: 1px solid #CCC;
}
input.money {
  width: 120px;
  padding: 1px;
  font: 400 1em verdana, sans-serif;
  color: #999;
  background: #EEE;
  background-image:url(../images/dollar-sign.png);
  background-repeat:no-repeat;
  padding-left: 20px;
  border: 1px solid #CCC;
}

input:focus,
input:hover,
textarea:focus,
textarea:hover,
select:focus,
select:hover {
  color: #000;
  background: #E7F1F3;
  border: 1px solid #888;
}

input.money:focus,
input.money:hover{
  color: #000;
  background-image:url(../images/dollar-sign.png);
  background-repeat:no-repeat;
/*background: #E7F1F3; */
  border: 1px solid #888;
}

input.noBorder,
input:focus.noBorder,
input:hover.noBorder {
  padding: 0;
  border: 0;
}

input.button {
  padding: 2px 5px;

  font: 400 0.9em verdana, serif;
  cursor: pointer;

  color: #fff;
  background: #FC3307;
  border-width: 1px;
  border-style: solid;
  border-color: #FF7800 #691300 #691300 #FF7800;
}

input.radio {
  background: none;
  border: 0px;
}

p.solid {
	border-style: solid;}

```

---

### Post by dhtseany on 2010-11-19
Update:
While forging ahead with other stuff I needed to get done, I noticed this:
```
<input type='checkbox' name='optionauto' value='option1' class='radio'/>Auto &nbsp;
```

...attached to the checkboxes. I'm wondering if the 'radio' class might have something to do with it.

Sean

---

### Post by dhtseany on 2010-11-19
Wow. So I get mad at all the screwed up form fields because that's what I was last working on so to temporarily see my checkboxes laid out correctly, I commented out my 3 "fix" lines.

While the input boxes marked as "money" are still 20px wider, everything is back to where it was before my attempted fix.

**Any suggestions how to eliminate the extra 20px caused by the padding-left: 20px;?**  

Thanks, guys! I'll always turn here first for this kind of thing!

Peace
Sean

---

