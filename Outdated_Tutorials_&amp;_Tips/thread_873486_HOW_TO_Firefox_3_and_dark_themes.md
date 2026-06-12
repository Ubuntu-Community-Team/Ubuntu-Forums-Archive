---
title: "HOW TO: Firefox 3 and dark themes"
date: 2008-07-29
forum: Outdated Tutorials &amp; Tips
---

### Post by element_G on 2008-07-29
A few dark GTK themes show how to fix the resulting Firefox's dark textboxes and forms, however those fixes don't work with Firefox 3. After a bit of googling I found an [_Arch Linux thread_ ]("http://bbs.archlinux.org/viewtopic.php?id=50409")that provided a solution. Since I couldn't find anything on Ubuntu Forums I thought I would post it here.

*Thanks to those who've helped me keep this updated with their feedback and tips*
*Updated 5 May 2009 ** still needs a bit of a touch-up***
 
:!:
[B][SIZE=3]According to aparigraha, a different stylish userstyle is needed for the lastest Firefox (3.0.10) please follow his instructions [here]("http://ubuntuforums.org/showpost.php?p=7220196&postcount=24")
[/SIZE][/B] 
**[SIZE=3]Step 1[/SIZE]. **Install the[COLOR=royalblue]_ [COLOR=black][Stylish Add-on]("https://addons.mozilla.org/en-US/firefox/addon/2108")[/COLOR]_[/COLOR]
 
****notes on using Stylish ****
The next 2 steps need you to create Styles in the Stylish add-on. 
To do this you can:
A. Click on the stylish icon to the right of the status bar > Manage Styles > Write
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=92268&stc=1&d=1226458810[/IMG]
OR
B. Tools > Add-ons > Scroll to Stylish and click Preferences > Manage Styles >Write
****back to the HOW-TO ****
 
 
 
**[SIZE=3]Step 2.[/SIZE] **Create (and Enable) "Nice Firefox Themes" Style in Stylish
 
```
/*******
 * Mac OS X look contribution by
 *   phiw - Philippe Wittenbergh (phiw@l-c-n.com) http://emps.l-c-n.com/
 *   hiro - NAKAJIMA Hiroki http://homepage.mac.com/travellers/software/Firefox/aquafirefox_en.html
 * 
 * last updated 2006.02.06
 *******/
 
/*******
 * Windows look contribution by
 *   akirasan - AkiraSan http://www.akirasan.net
 *       Use this code at your own risk.
 *       Making a backup of your valuable data is never a bad idea.
 *       I am not responsible for any data loss, physical injuries, or mental traumas resulting from using this code.
 *       If you want to further develop, improve or modify this code, feel free to do so.
 *       I'll appreciate feedback and if you make this code available for distribution,
 *       a link back to my blog (http://www.akirasan.net)
 * 
 * last updated 28.05.2007
 *******/
 
 
/* Set default namespace to HTML */
@namespace url(http://www.w3.org/1999/xhtml); 
@namespace xul url(http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul);
 
  /***********************  ~364  ***********************/
  /* common features of radio buttons and check boxes */
 
  input[type="radio"],
  input[type="checkbox"] {
      background-color: transparent  !important;
      border:           none         !important;
  }
 
  input[type="radio"][disabled],
  input[type="radio"][disabled]:active,
  input[type="radio"][disabled]:hover,
  input[type="radio"][disabled]:hover:active,
  input[type="checkbox"][disabled],
  input[type="checkbox"][disabled]:active,
  input[type="checkbox"][disabled]:hover,
  input[type="checkbox"][disabled]:hover:active {
      background-color: transparent  !important;
      color:            inherit      !important;
      border:           none         !important;
  }
 
  input[type="checkbox"]:focus,
  input[type="radio"]:focus {
      border-style: none  !important;
  }
 
  input[type="checkbox"]:hover:active,
  input[type="radio"]:hover:active {
      background-color:  transparent  !important;
      border-style:      none         !important;
  }
 
/*  *|*::-moz-radio {
      background-color: transparent  !important;
  }*/
 
 
 
  /* --------------------------------------------------------------------------
   *
   *    modified by phiw - Philippe Wittenbergh. phiw@l-c-n.com  emps.l-c-n.com
   *
   * -------------------------------------------------------------------------- */
 
  /*  --- Font Setting --- */
 
  html select,
  html input,
  html input[type="submit"],
  html input[type="reset"],
  html input[type="password"],
  html input[type="file"],
  html input[type="text"],
  html input:not([type]) {
      font-size: small;
  }
 
 
  /* --- Color Setting --- */
 
  html input[type="reset"],
  html input[type="submit"],
  html input[type="file"] {
      color: #1e1e1e !important; /* soft black */
  }
 
  html input,
  html textarea {
      color: #1e1e1e;
  }
 
  html button,
  html input[type="button"] {
      color: #1e1e1e !important;
  }
 
  /* --- Input, textarea  --- */
 
  html input,
  html input[type="text"],
  html input[type="password"],
  html textarea {
      background-color: -moz-Field;
      background-repeat: repeat-x;
      background-position: 0 0;
      -moz-border-radius: 0;
      padding: 1px 0 1px 3px;
  }
 
  html input,
  html textarea {
      border-top: 1px solid #616365;
      border-right: 1px solid #a0a3a5;
      border-bottom: 1px solid #bbbdbf; 
      border-left: 1px solid #616365;
  }
 
  *[dir="rtl"] input[type="text"],
  *[dir="rtl"] input[type="password"],
  *[dir="rtl"] input:not([type]),
  *[dir="rtl"] textarea {
      padding: 1px 3px 1px 0;
  }
 
  html input[type="image"] {
      border:none;
      background-image:none;
      padding:0;
  }
 
  /* --- Radio Buttons --- */
/*  *|*::-moz-radio {
      border: 0 none !important;
      background-color: transparent !important;
  }*/
 
  html input[type="radio"] {
      -moz-appearance: none;
      width: 13px !important;
      height: 13px !important;
      margin: 3px 5px 0;
      background: transparent no-repeat center center  !important;
      vertical-align: baseline;
      border: 0 none !important;
      outline:none !important;
      -moz-border-radius: 0 !important;
  }
 
  html input[type="radio"]:checked {
      background: transparent no-repeat center center  !important;
      border: 0 none !important;
  }
 
 
  /* --- Check Boxes --- */
 
  html input[type="checkbox"] {
      width: 13px !important;
      height:13px !important;
      margin: 1px 2px 3px 3px;
      vertical-align: text-bottom;
      -moz-border-radius: 0 !important;
      -moz-appearance: none;            /*akirasan*/
  }
 
  html input[type="checkbox"],
  html input[type="checkbox"]:checked{
      background: transparent no-repeat center center  !important;
      border: 0 none !important;
  }
 
  html input[type="radio"]:focus,
  html input[type="checkbox"]:focus {
      border: 0 none !important;
  }
 
  /* --- Buttons, Submit, Reset --- */
 
  html input[type="reset"],
  html input[type="submit"],
  html input[type="file"] > input[type="button"] {
      background: #efeded repeat-x 50% 65%  !important;
      text-indent: 0 !important; /* beat those pesky ImageReplacement techniques */
      padding: 1px 4px !important;
      margin: 0;
      border: 2px solid !important;
      -moz-border-bottom-colors: #616365 #cecece;
      -moz-border-left-colors: #797b7f #fff;
      -moz-border-right-colors: #616365 #cecece;
      -moz-border-top-colors: #797b7f #fff;
      -moz-border-radius: 1px !important;
      letter-spacing:0 !important
  }
 
  html button,
  html input[type="button"],
  html button[disabled],
  html input[type="button"][disabled] { /* less strict, allows author styling */
      background: #efeded repeat-x 50% 65%;
      text-indent: 0;
      padding: 1px 4px;
      margin: 0;
      border: 2px solid;
      -moz-border-bottom-colors: #616365 #cecece;
      -moz-border-left-colors: #797b7f #e8e8e8;
      -moz-border-right-colors: #616365 #cecece;
      -moz-border-top-colors: #797b7f #e8e8e8;
      letter-spacing:0;
      -moz-border-radius: 1px;
  }
  button[disabled]:active,
  input[type="button"][disabled]:active {
      padding: 1px 4px;
      border: 2px solid;
  }
 
  /* --- input type=file --- */
 
  html input[type="file"] {
      background:transparent !important;
  }
 
  html input[type="file"] > input[type="text"] {
      margin: 0 1px 0 0;
      background-color: #fff !important;
  }
 
  html input[type="file"] > input[type="button"] {
      margin: 0 1px !important;
  }
 
  /* --- Select Options --- */
 
/*  *|*::-moz-display-comboboxcontrol-frame {
      padding: 1px 4px;
  }
 
  *|*::-moz-dropdown-list {
      border: none !important;
      border-color:transparent  !important;
      background-color: #fff !important;
  }*/
 
  html select {
      color: -moz-FieldText;
      background: #fff ;
      border: 1px solid #797b7f;
      border-color: #797b7f #999 #999 #797b7f;
      padding: 0;
      direction: ltr;
  }
  *[dir="rtl"] select,
  * select[dir="rtl"] {
      direction: rtl;
  }
 
  html select[multiple],
  html select[size],
  html select[size][multiple] {
      padding: 0;
  }
 
  html select:not([size]):not([multiple]),
  html select[size],
  html select[size="1"] {
  /*background: rgb(246, 246, 246) url("resource://gre/res/forms-grad.png") repeat-x bottom right !important;*/
      background: rgb(246, 246, 246) repeat-x bottom right  !important;
      color: #2e2e2e !important;
      height:auto !important;
      border: 2px solid !important;
      -moz-border-top-colors: #797b7f #fff;
      -moz-border-right-colors: #616365 #cecece;
      -moz-border-bottom-colors: #616365 #cecece;
      -moz-border-left-colors: #797b7f #fff;
      -moz-box-sizing: border-box !important;
      -moz-border-radius: 1px !important;
      padding:0 !important;
  }
  html select:not([size]):not([multiple]):focus,
  html select[size]:focus,
  html select[size="1"]:focus,
  html select:not([size]):not([multiple]):hover:active,
  html select[size]:hover:active,
  html select[size="1"]:hover:active {
      -moz-border-top-colors: #616365 #fff;
      -moz-border-right-colors: #797b7f #cecece;
      -moz-border-bottom-colors: #797b7f #cecece;
      -moz-border-left-colors: #616365 #fff;
  }
 
  html optgroup,
  html option {
      background:transparent;
      font-family:inherit;
      font-size:inherit;
  }
 
  html optgroup:before {
      font-style:normal;
      font-weight:normal;
      padding: 2px 5px 0 5px;
  }
  html select:not([size]):not([multiple]) optgroup:before,
  html select[size] optgroup:before,
  html select[size="1"] optgroup:before {
      color: #727272;
  }
 
  html select:not([size]):not([multiple]) option,
  html select[size] option,
  html select[size="1"] option,
  html select:not([size]):not([multiple]) optgroup,
  html select[size] optgroup,
  html select[size="1"] optgroup {
      background: transparent !important;
      color: inherit !important;
  }
  html select:not([size]):not([multiple]) option:hover,
  html select[size] option:hover,
  html select[size="1"] option:hover {
      background-color: Highlight ! important;
      color: HighlightText ! important;
  }
  html option:checked {
      background-color: Highlight ! important;
      color: HighlightText ! important;
  }
 
 
  html select > input[type="button"],
  /*html select > input[type="button"]:focus,*/
  html select > input[type="button"]:hover:active {
      background-color: transparent !important;
      background-repeat: no-repeat !important;
      background-position:  45% 50% !important;
      outline: none;
      margin: 0 !important;
      border-width: 0 2px !important;
      border-style: solid !important;
      -moz-border-left-colors: #a3a3a3 transparent !important;
      -moz-border-right-colors: transparent transparent !important;
      padding: 0 6px !important;
  }
 
  *[dir="rtl"] select > input[type="button"],
  *[dir="rtl"] select > input[type="button"]:hover:active,
  select[dir="rtl"] > input[type="button"],
  select[dir="rtl"] > input[type="button"]:hover:active {
      -moz-border-right-colors: #a3a3a3 transparent !important;
      -moz-border-left-colors: transparent transparent !important;
      background-position:  60% 50% !important;
  }
 
  /* -- focus ring - mac specific code -- maybe use outline: 1px dotted invert for Linux ? -- disabled, this reverts to the default behaviour, I think. */
 
  html input[type="reset"]:focus,
  html input[type="submit"]:focus {
      color:#262626 !important;
  }
 
  /* --- disabled widgets --- */
 
 
  html input[type="reset"][disabled],
  html input[type="submit"][disabled],
  html input[type="file"][disabled],
  html select[disabled],
  html select[disabled] option,
  html option[disabled] {
      color:#727272 !important;
  }
  html input[disabled],
  html textarea[disabled],
  html option[disabled],
  html optgroup[disabled],
  html select[disabled],
  html select[disabled]>* {
      -moz-user-input: disabled;
      -moz-user-focus: ignore;
  }
 
  html select[disabled] > input[type="button"] {
      border:none;
      border-left:2px solid;
      -moz-border-left-colors: #b3b3b3 transparent;
  }
 
  html option[disabled],
  html optgroup[disabled] {
      background-color: transparent;
  }
 
  html input[type="radio"][disabled],
  html input[type="radio"][disabled]:active,
  html input[type="radio"][disabled]:hover,
  html input[type="radio"][disabled]:hover:active,
  html input[type="checkbox"][disabled],
  html input[type="checkbox"][disabled]:active,
  html input[type="checkbox"][disabled]:hover,
  html input[type="checkbox"][disabled]:hover:active {
      border: 0 none !important;
      background-color: transparent !important;
      outline-width: 0 !important;
  }
 
  html select[disabled],
  html input[disabled],
  html textarea[disabled],
  html button[disabled],
  html input[type="checkbox"][disabled],
  html input[type="radio"][disabled],
  html input[type="button"][disabled],
  html input[type="reset"][disabled],
  html input[type="submit"][disabled] {
      opacity: 0.6;
  }
 
  html input[type="file"][disabled] > * {
      opacity:1.0 !important;
  }
 
 
 
  /****************************************************************************\
    :CHANGES: void
  \****************************************************************************/
 
  input[type="file"] > input[type="text"],
  html input:not([type]),
  html input[type="text"],
  html input[type="password"],
  html textarea {
      -moz-border-radius: 3px;
  }
 
  /**
   *  BASE 64 IMAGES
   */
  html input,
  html input[type="text"],
  html input[type="password"],
  html textarea {
      background-image: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAQAAAAECAYAAACp8Z5+AAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEgAACxIB0t1+/AAAABV0RVh0Q3JlYXRpb24gVGltZQAwNC45LjE4xKRlPwAAACF0RVh0U29mdHdhcmUATWFjcm9tZWRpYSBGaXJld29ya3MgNC4w6iYndQAAACJJREFUeJxjXLxk2WYGJMDCwMDQiyzA+P//f2Q+AxMDGgAAJwEGM2kcXr8AAAAASUVORK5CYII=");
  }
  html input[type="radio"] {
      background-image: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAA0AAAANCAYAAABy6+R8AAAABGdBTUEAANbY1E9YMgAAABl0RVh0U29mdHdhcmUAQWRvYmUgSW1hZ2VSZWFkeXHJZTwAAAG9SURBVCjPfZLLaiJBFIYrBHyK7GYZHPIAWc4ziCIYRFy4cKOgYCO46IUuFDR4GUTTm8aF4kaia0FFwY1CIl5oFFva0YwGaTD2JWdOCQFJ4hR8FFWn/lOnzl8EAMgHJpPJaDabi1arVbTZbGC320Wn01l0uVzG03Mfhw0IY7FYlHA4PG+1WvJwOIR2uy0nEgnR7XYrHo+H8fl8l6eie8y86fV6qqZp8JnBYKAGAoG/DMPcH0UouMWStEaj8YYDztHtdt9CoZDGsuwtQQHv9/ufMRvIsnwWGk+lUk+RSIQn9NE8z79g/dDv90EURViv17DZbI4zXdN9Gq9UKi/RaFQk+JZDvV5XaSbKZDL5lvF4DJ1OR43H4wficDikarW6nU6nMJvNQJKkL9B9Gm82m9t0Ov2HeL3ex1gsJqxWK9jtdmeh8XK5LHAc90geOO6O+jAajf7bvcVioWUyGaVQKPwie0X/GQwGC8gWa9dxwGfm87mey+W22Wz299GnvfJuxCw/0DgWfdBLpdIrFS+XSxAEQa/Vaq94g44CNp/PG46iw169RtevcHGBxt2gD0Vsq4RdgmQyKaGgiIKb07/3DxehBztkriL/AAAAAElFTkSuQmCC")  !important;
  }
  html input[type="radio"]:checked {
      background-image: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAA0AAAANCAYAAABy6+R8AAAABGdBTUEAANlkkQC7WgAAACBjSFJN    AAB5FwAAgOgAAOvlAACGZQAAgC4AAN3gAAA5EwAALfFDOSc6AAAACXBIWXMAAAsTAAALEwEAmpwYAAABx0lEQVQoz31SOWsCURB+BNbC3xFSp9RGGzvriCAICoImneAWaqULshALC8HEAwQjJForsTCFCBtZzCLieuGBFh6YwlgIKpN5SxI0kDz4ePtm5pvjmyUAQL5hMpnOzWYzb7FYClarVbTZbAWHw8G7XK7z47jvYAZhx0ApFov16vX6x3A4BEmSPtLpdN/tdksIO8uyZ8ckFrNJnU5nt9/v4TcGg8EuEAi8+Xw+ViEh4RLbkURR3OKBv9BoNLZIlDiOuyQ4AxcMBl9lWYbNZgPdbheMRiOoVCrlpm9qp/5UKiXwPM8ROnQ+n18KgkCzgU6nw/rkBxqNRrFTf7FYXIbD4QJBhWrVanVHM1Go1eoTEsMw0O/3odfrAY6wi0QiAnE6nS/lcvl9NBrBeDwGvV5/QtJqtYqd+mu12nsikagQr9d7jx/NxWIB6/UaWq0WGAwGhUBv+qZ26sf2mpmHzB15fHq68ng8TdzLv+rN5/N9Mpls5nI5rbInlPEWVZEnk8kBD/zGbDY7ZLNZGTvy/SyXwu/334RCoXapVFpS8mq1gul0eqhUKkus0I7H49coOXNC+qp4gRV5lPUZVRKj0egz/lY8Ei6O4z4Bnd/QpvegPQoAAAAASUVORK5CYII=")  !important;
  }
  html input[type="checkbox"],
  html input[type="checkbox"]:checked{
      background-image: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAA0AAAANCAYAAABy6+R8AAAABGdBTUEAANbY1E9YMgAAABl0RVh0U29mdHdhcmUAQWRvYmUgSW1hZ2VSZWFkeXHJZTwAAAE6SURBVCjPhZI9bipBEISremYX9g82sHPkKzglQYgrcIF3Bl/ByTuUJRLA+BgkpMgae0fTPY6QLNmYlkodfWr1p+J6va4BPAFYkGxFBN/jnLvkXURenHP/PYCn1Wr1b7lc3vd9P8aVOZ/Pn/v9/mG328EDWMzn87vZbDbOOV9j0Pf9OMZ4dzgcFp5kN51Oq5QS/oJIom3byjnXeTOjqkJVQfJXkCTMDKoKM6MnyZQShmGAiFy9ZGZIKQEAPUmEEBBCgHPuKqSqAAARgW+aRoqiAMmbUM4ZdV2L77pOyrJEWZY3oRgjqqoSP5lMfFVV8N7f/Mk5h6ZpvG/bdsg5p9FoJCIif9izlJLVdT1IURSvx+PxQ1Xzt8r8iJnl0+n0ISKvPsb4vNlsuu12+0iyuRi67IsgkkFV30IIz18cwI1NeExqHQAAAABJRU5ErkJggg==")  !important;
  }
  html input[type="reset"],
  html input[type="submit"],
  html input[type="file"] > input[type="button"] {
      background-image: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAoAAAA8CAYAAABfESsNAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEgAACxIB0t1+/AAAABZ0RVh0Q3JlYXRpb24gVGltZQAwNS4xMS4yN6/1yKEAAAAhdEVYdFNvZnR3YXJlAE1hY3JvbWVkaWEgRmlyZXdvcmtzIDQuMOomJ3UAAABhSURBVHic7dPBCYAwDEZhW1xCwZS6/1JqelYHCHEC5R0EEfKfP94hkOTuYweWCQoYMGDAgPfr9+NkcFGFcGvfFSFctTmB/I61TAzOIi8Xa6FFYcVkZgMq5swu9IdXCPi4C6HeHFixIGPzAAAAAElFTkSuQmCC")  !important;
  }
 
  html input[type="reset"]:focus,
  html input[type="submit"]:focus,
  html input[type="reset"]:hover,
  html input[type="submit"]:hover,
  html input[type="reset"]:hover:active,
  html input[type="submit"]:hover:active {
      background-image: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAoAAAA8CAYAAABfESsNAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEgAACxIB0t1+/AAAABZ0RVh0Q3JlYXRpb24gVGltZQAwNS4xMS4yN6/1yKEAAAAhdEVYdFNvZnR3YXJlAE1hY3JvbWVkaWEgRmlyZXdvcmtzIDQuMOomJ3UAAABjSURBVHic7dPBCYBADERRN9iEu7CWov23oWL2JnoOsQLl30TInB8ZGEhy97kDEYICBgwYMOBz+uO8GFx3pbBBqBTS6oVWb9qcQL5jLQODY4awlvxRdTKzCV0UYQv94RUCvuYGx8ocsZqoiv8AAAAASUVORK5CYII=")  !important;
  }
 
  html button,
  html input[type="button"],
  html button[disabled],
  html input[type="button"][disabled] { /* less strict, allows author styling */
      background-image: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAoAAAA8CAYAAABfESsNAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEgAACxIB0t1+/AAAABZ0RVh0Q3JlYXRpb24gVGltZQAwNS4xMS4yN6/1yKEAAAAhdEVYdFNvZnR3YXJlAE1hY3JvbWVkaWEgRmlyZXdvcmtzIDQuMOomJ3UAAABhSURBVHic7dPBCYAwDEZhW1xCwZS6/1JqelYHCHEC5R0EEfKfP94hkOTuYweWCQoYMGDAgPfr9+NkcFGFcGvfFSFctTmB/I61TAzOIi8Xa6FFYcVkZgMq5swu9IdXCPi4C6HeHFixIGPzAAAAAElFTkSuQmCC");
  }
  html button:focus,
  html input[type="button"]:focus,
  html button:hover,
  html input[type="button"]:hover,
  html button:hover:active,
  html input[type="button"]:hover:active {
      background-image: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAoAAAA8CAYAAABfESsNAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEgAACxIB0t1+/AAAABZ0RVh0Q3JlYXRpb24gVGltZQAwNS4xMS4yN6/1yKEAAAAhdEVYdFNvZnR3YXJlAE1hY3JvbWVkaWEgRmlyZXdvcmtzIDQuMOomJ3UAAABjSURBVHic7dPBCYBADERRN9iEu7CWov23oWL2JnoOsQLl30TInB8ZGEhy97kDEYICBgwYMOBz+uO8GFx3pbBBqBTS6oVWb9qcQL5jLQODY4awlvxRdTKzCV0UYQv94RUCvuYGx8ocsZqoiv8AAAAASUVORK5CYII=");
  }
  html select:not([size]):not([multiple]),
  html select[size],
  html select[size="1"] {
      background-image: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAARCAYAAAAcw8YSAAAABGdBTUEAANbY1E9YMgAAABl0RVh0U29mdHdhcmUAQWRvYmUgSW1hZ2VSZWFkeXHJZTwAAABZSURBVHjaYvr//z8DQAAxMQIBQAAxMTAwMAIEEIhgAgggMAsggMAEQACBuQABBCYAAgjMBQggMAsggMAsgAACswACCMwCCCAwCyCAwCyAAAITAAEEJgACDAACqAM55WzqjgAAAABJRU5ErkJggg==")  !important;
  }
  html select > input[type="button"],
  /*html select > input[type="button"]:focus,*/
  html select > input[type="button"]:hover:active {
      background-image: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABMAAAAZCAYAAADTyxWqAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAAK8AAACvABQqw0mAAAACF0RVh0U29mdHdhcmUATWFjcm9tZWRpYSBGaXJld29ya3MgNC4w6iYndQAAALdJREFUeJzt1E0KgzAQhuHXaqEV3HSVg8z9TzBXEXHTH6ykmxSETkZbsii0szMZH744ahVjpFTtikl/7KNq1hpEpAZqYFbV2et1kyWoA25Al67fxxbQkJaGNdDEDOhZLphLVhvQEjQxbwAnYG+sT7kbqpLfpplMRBqgJZ/srKr3TVhCRidEC7xguQFMQMjsBTLPzcTSEXoDDEBvHdFLZoEuBBumKSIH4AhcVPXq9RZ9Nb73f/Yj2AOpzz2UFWQSawAAAABJRU5ErkJggg==")  !important;
  }
```[SIZE=3]**Step 3.**[/SIZE] Create (and Enable) "Fix Dark Textboxes" Style in Stylish
 
```
@namespace url(http://www.w3.org/1999/xhtml);
 
@-moz-document url-prefix(http), url-prefix(file) {
 
pre, input, textarea {
   color: black !important;
   background: white !important;
   border-left-color: gray !important;
   border-right-color: gray !important;
   border-top-color: gray !important;
   border-bottom-color: gray !important;
}
 
/* Uncomment this part if you also want to apply to forms and the like. */
input:not([type="button"]):not([type="checkbox"])
:not([type="submit"]):not([type="reset"]), 
select {
    color: black !important;
    border-left-color: gray !important;
    border-right-color: gray !important;
    border-top-color: gray !important;
    border-bottom-color: gray !important;
}
 
}
```[B]
[SIZE=3]Step 4.[/SIZE][/B] Back up original forms.css in /usr/lib/xulrunner-x.x.x.x/res [I]
(UPDATED: 5 May 2009 to reflect latest xulrunner)[/I]
 
```
sudo cp /usr/lib/xulrunner-1.9.0.10/res/forms.css /usr/lib/xulrunner-1.9.0.10/res/forms.css.back
```[B]
[SIZE=3]Step 5[/SIZE]. [/B]Create a new forms.css 
 
```
sudo gedit /usr/lib/xulrunner-1.9.0.10/res/forms.css
```(KDE users type kwrite instead of gedit)
 
Paste the following as your new forms.css
```
/* ***** BEGIN LICENSE BLOCK *****
 * Version: MPL 1.1/GPL 2.0/LGPL 2.1
 *
 * The contents of this file are subject to the Mozilla Public License Version
 * 1.1 (the "License"); you may not use this file except in compliance with
 * the License. You may obtain a copy of the License at
 * http://www.mozilla.org/MPL/
 *
 * Software distributed under the License is distributed on an "AS IS" basis,
 * WITHOUT WARRANTY OF ANY KIND, either express or implied. See the License
 * for the specific language governing rights and limitations under the
 * License.
 *
 * The Original Code is mozilla.org code.
 *
 * The Initial Developer of the Original Code is
 * Netscape Communications Corporation.
 * Portions created by the Initial Developer are Copyright (C) 1998
 * the Initial Developer. All Rights Reserved.
 *
 * Contributor(s):
 *
 * Alternatively, the contents of this file may be used under the terms of
 * either of the GNU General Public License Version 2 or later (the "GPL"),
 * or the GNU Lesser General Public License Version 2.1 or later (the "LGPL"),
 * in which case the provisions of the GPL or the LGPL are applicable instead
 * of those above. If you wish to allow use of your version of this file only
 * under the terms of either the GPL or the LGPL, and not to allow others to
 * use your version of this file under the terms of the MPL, indicate your
 * decision by deleting the provisions above and replace them with the notice
 * and other provisions required by the GPL or the LGPL. If you do not delete
 * the provisions above, a recipient may use your version of this file under
 * the terms of any one of the MPL, the GPL or the LGPL.
 *
 * ***** END LICENSE BLOCK ***** */
 
/** 
  Styles for old GFX form widgets
 **/ 
 
 
@namespace url(http://www.w3.org/1999/xhtml); /* set default namespace to HTML */
@namespace xul url(http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul);
 
*|*::-moz-fieldset-content {
  display: block;
  height: 100%;   /* Need this so percentage heights of kids work right */
}
 
/* miscellaneous form elements */
 
legend {
  padding-left: 2px;
  padding-right: 2px;
  border: none;
  position: static ! important;
  float: none ! important;
  width: -moz-fit-content ! important;
  min-width: 0 ! important;
  max-width: none ! important;
  height: auto ! important;
  min-height: 0 ! important;
  max-height: none ! important;
  white-space: nowrap;
}
 
fieldset {
  display: block;
  margin-left: 2px;
  margin-right: 2px;
  padding: 0.35em 0.625em 0.75em;
  border: 2px groove ThreeDFace;
}
 
label {
  cursor: default;
}
 
/* default inputs, text inputs, and selects */
 
/* Note: Values in nsNativeTheme IsWidgetStyled function 
   need to match textfield background/border values here */
 
input {
  /* The sum of border-top, border-bottom, padding-top, padding-bottom
     must be the same here, for buttons, and for <select> (including its
     internal padding magic) */
  padding: 1px 0 1px 0;
  /*border: 2px inset ThreeDFace;
  background-color: -moz-Field;*/
  color: -moz-FieldText;
  font: -moz-field;
  text-rendering: optimizeLegibility;
  line-height: normal !important;
  text-align: start;
  text-transform: none;
  word-spacing: normal;
  letter-spacing: normal;
  cursor: text;
  -moz-binding: url("chrome://global/content/platformHTMLBindings.xml#inputFields");
  text-indent: 0;
  -moz-user-select: text;
}
 
input > .anonymous-div {
  white-space: pre;
}
 
textarea {
  margin: 1px 0 1px 0;
  border: 2px inset ThreeDFace;
  background-color: -moz-Field;
  color: -moz-FieldText;
  font: medium -moz-fixed;
  text-rendering: optimizeLegibility;
  text-align: start;
  text-transform: none;
  word-spacing: normal;
  letter-spacing: normal;
  vertical-align: text-bottom;
  cursor: text;
  -moz-binding: url("chrome://global/content/platformHTMLBindings.xml#textAreas");
  text-indent: 0;
  -moz-user-select: text;
}
 
textarea > scrollbar {
  cursor: default;
}
 
textarea > .anonymous-div,
input > .anonymous-div {
  overflow: auto;
  border: 0px !important;
  /* The 1px horizontal padding is for parity with Win/IE */
  padding: 0px 1px;
  margin: 0px;
  /* XXXldb I'm not sure if we really want the 'text-decoration: inherit',
     but it's needed to make 'text-decoration' "work" on text inputs. */
  text-decoration: inherit;
  ime-mode: inherit;
}
 
input:-moz-read-write,
textarea:-moz-read-write {
  -moz-user-modify: read-write !important;
}
 
select {
  margin: 0;
  border-color: ThreeDFace;
  background-color: -moz-Field;
  color: -moz-FieldText;
  font: -moz-list;
  line-height: normal !important;
  white-space: nowrap !important;
  text-align: start; 
  cursor: default;
  -moz-box-sizing: border-box;
  -moz-user-select: none;
  border-width: 2px;
  border-style: inset;
  text-indent: 0;
  overflow: -moz-hidden-unscrollable;
}
 
/* Need the "select[size][multiple]" selector to override the settings on
   'select[size="1"]', eg if one has <select size="1" multiple> */
 
select[size],
select[multiple],
select[size][multiple] {
  /* Different alignment and padding for listbox vs combobox */
  vertical-align: text-bottom;
  padding: 1px 0 1px 0;
}
 
select[size],
select[size="1"] {
  /* Except this is not a listbox */
  vertical-align: baseline;
  padding: 0;
}
 
select > input[type="button"] {
  width: 12px;
  height: 12px;
  white-space: nowrap;
  position: static !important;
  background-image: url("arrow.gif") !important; 
  background-repeat: no-repeat !important;
  background-position: center !important;
 
  /* Make sure to size correctly if the combobox has a non-auto height. */
  height: 100% ! important;
  -moz-box-sizing: border-box ! important;
 
  /*
    Make sure to align properly with the display frame.  Note that we
    want the baseline of the combobox to match the baseline of the
    display frame, so the dropmarker is what gets the vertical-align.
  */
  vertical-align: top !important;
}
 
select > input[type="button"]:active {
  background-image: url("arrowd.gif") !important; 
}
 
select:empty {
  width: 2.5em;
}
 
*|*::-moz-display-comboboxcontrol-frame {
  overflow: -moz-hidden-unscrollable;
  /* This top/bottom padding plus the combobox top/bottom border need to
     add up to the top/bottom borderpadding of text inputs and buttons */ 
  padding-top: 1px;
  padding-bottom: 1px;
  -moz-padding-start: 4px;
  -moz-padding-end: 0;
  background-color: inherit;
  color: inherit;
  white-space: nowrap;
  text-align: inherit;
  -moz-user-select: none;
  /* Make sure to size correctly if the combobox has a non-auto height. */
  height: 100% ! important;
  -moz-box-sizing: border-box ! important;
}
 
select::-moz-scrolled-content {
  display: block !important;
}
 
option {
  display: block;
  float: none !important;
  position: static !important;
  min-height: 1em;
  line-height: normal !important;
  -moz-user-select: none;
  text-indent: 0;
  white-space: nowrap !important;
}
 
select > option {
  padding-top : 0;
  padding-bottom: 0;
  -moz-padding-start: 3px;
  -moz-padding-end: 5px;
}
 
option:checked {
  background-color: -moz-html-cellhighlight !important;
  color: -moz-html-cellhighlighttext !important;
}
 
select:focus > option:checked,
select:focus > optgroup > option:checked {
  background-color: Highlight ! important;
  color: HighlightText ! important;
}
 
optgroup {
  display: block;
  float: none !important;
  position: static !important;
  font: -moz-list;
  line-height: normal !important;
  font-style: italic;
  font-weight: bold;
  font-size: inherit;
  -moz-user-select: none;
  text-indent: 0;
  white-space: nowrap !important;
}
 
optgroup > option {
  -moz-padding-start: 20px;
  font-style: normal;
  font-weight: normal;
}
 
optgroup:before {
  display: block;
  content: attr(label);
}
 
*|*::-moz-dropdown-list {
  z-index: 2147483647;
  background-color: inherit;
  -moz-user-select: none;
  position: static !important;
  float: none !important;
 
  /*
   * We can't change the padding here, because that would affect our
   * intrinsic width, since we scroll.  But at the same time, we want
   * to make sure that our left border+padding matches the left
   * border+padding of a combobox so that our scrollbar will line up
   * with the dropmarker.  So set our left border to 2px.
   */
  border: 1px outset black !important;
  border-left-width: 2px ! important;
} 
 
input[disabled],
textarea[disabled],
option[disabled],
optgroup[disabled],
select[disabled] {
  -moz-user-input: disabled;
  -moz-user-focus: ignore;
  color: GrayText;
  background-color: ThreeDFace;
  cursor: inherit;
}
 
option[disabled],
optgroup[disabled] {
  background-color: transparent;
}
 
/* hidden inputs */
input[type="hidden"] {
  display: none;
  padding: 0;
  border: 0;
  cursor: auto;
  -moz-user-focus: ignore;
  -moz-binding: none;
}
 
/* image buttons */
input[type="image"] {
  padding: 0;
  border: none;
  background-color: transparent;
  font-family: sans-serif;
  font-size: small;
  cursor: pointer;
  -moz-binding: none;
}
 
input[type="image"][disabled] {
  cursor: inherit;
}
 
input[type="image"]:focus {
  /* Don't specify the outline-color, we should always use initial value. */
  outline: 1px dotted;
}
 
/* file selector */
input[type="file"] {
  white-space: nowrap;
  cursor: default;
  -moz-binding: none;
 
  padding: 0 !important;
  border-style: none !important;
}
 
input[type="file"] > input[type="text"] {
  border-color: gray;
  -moz-border-radius: 0 !important;
  border-top: 1px solid #616365;
  border-right: 1px solid #a0a3a5;
  border-bottom: 1px solid #bbbdbf;
  border-left: 1px solid #616365;
  color: inherit;
  font-size: inherit;
  letter-spacing: inherit;
}
 
/* button part of file selector */
input[type="file"] > input[type="button"] {
  height: inherit;
  font-size: inherit;
  letter-spacing: inherit;
}
 
/* radio buttons */
input[type="radio"] {
  width: 13px;
  height: 13px;
  margin: 3px 3px 0px 5px;
  padding: 0 !important;
  cursor: default;
  -moz-binding: none;
 
  -moz-border-radius: 100% !important;
}
 
/* check boxes */
input[type="checkbox"] {
  width: 13px;
  height: 13px;
  margin: 3px 3px 3px 4px;
  padding: 0 !important;
  cursor: default;
  -moz-binding: none;
 
  -moz-border-radius: 0 !important;
}
 
/* common features of radio buttons and check boxes */
 
input[type="radio"],
input[type="checkbox"] {
  /* same colors as |input| rule, but |!important| this time. */
  -moz-box-sizing: border-box;
  background-color: -moz-Field /* ! important */;
  color: -moz-FieldText /* ! important */;
  border: 2px inset ThreeDFace /* ! important */;
}
 
input[type="radio"][disabled],
input[type="radio"][disabled]:active,
input[type="radio"][disabled]:hover,
input[type="radio"][disabled]:hover:active,
input[type="checkbox"][disabled],
input[type="checkbox"][disabled]:active,
input[type="checkbox"][disabled]:hover,
input[type="checkbox"][disabled]:hover:active {
  padding: 1px;
  border: 1px inset ThreeDShadow /* ! important */;
  /* same as above, but !important */
  color: GrayText /* ! important */;
  background-color: ThreeDFace /* ! important */;
  cursor: inherit; 
}
 
input[type="checkbox"]:focus,
input[type="radio"]:focus {
  border-style: groove !important;
}
 
input[type="checkbox"]:hover:active,
input[type="radio"]:hover:active {
  background-color: ThreeDFace /* ! important */;
  border-style: inset !important;
}
 
*|*::-moz-radio {
  width: 4px;
  height: 4px;
  background-color: -moz-FieldText /* ! important */;
  -moz-border-radius: 3px;
}
 
/* buttons */
 
/* Note: Values in nsNativeTheme IsWidgetStyled function 
   need to match button background/border values here */
 
button, 
input[type="reset"],
input[type="button"],
input[type="submit"] { 
  /* The sum of border-top, border-bottom, padding-top, padding-bottom
     must be the same here, for text inputs, and for <select>.  For
     buttons, make sure to include the -moz-focus-inner border/padding. */
  padding: 0px 6px 0px 6px;
/*  border: 2px outset ButtonFace;
  background-color: ButtonFace; */
  color: ButtonText; 
  font: -moz-button;
  line-height: normal !important;
  white-space: pre;
  cursor: default;
  -moz-box-sizing: border-box;
  -moz-user-select: none;
  -moz-binding: none;
  text-align: center;
}
 
button {
  /* Buttons should lay out like "normal" html, mostly */
  white-space: inherit;
  text-indent: 0;
}
 
*|*::-moz-button-content {
  display: block;
}
 
button:hover,
input[type="reset"]:hover,
input[type="button"]:hover,
input[type="submit"]:hover {
  background-color: -moz-buttonhoverface;
  color: -moz-buttonhovertext;
}
 
button:active:hover,
input[type="reset"]:active:hover,
input[type="button"]:active:hover,
input[type="submit"]:active:hover {
  padding: 0px 5px 0px 7px;
  border-style: inset;
  background-color: ButtonFace;
  color: ButtonText;
}
 
button::-moz-focus-inner,
input[type="reset"]::-moz-focus-inner,
input[type="button"]::-moz-focus-inner,
input[type="submit"]::-moz-focus-inner,
input[type="file"] > input[type="button"]::-moz-focus-inner {
  padding: 0px 2px 0px 2px;
  border: 1px dotted transparent;
}
 
button:focus::-moz-focus-inner,
input[type="reset"]:focus::-moz-focus-inner,
input[type="button"]:focus::-moz-focus-inner,
input[type="submit"]:focus::-moz-focus-inner,
input[type="file"] > input[type="button"]:focus::-moz-focus-inner {
  border-color: ButtonText;
}
 
button[disabled]:active, button[disabled],
input[type="reset"][disabled]:active,
input[type="reset"][disabled],
input[type="button"][disabled]:active,
input[type="button"][disabled],
select[disabled] > input[type="button"],
select[disabled] > input[type="button"]:active,
input[type="submit"][disabled]:active,
input[type="submit"][disabled] {
  /* The sum of border-top, border-bottom, padding-top, padding-bottom
     must be the same here and for text inputs */
  padding: 0px 6px 0px 6px;
  border: 2px outset ButtonFace;
  color: GrayText;
  cursor: inherit; 
}
 
 /*
  * Make form controls inherit 'unicode-bidi' transparently as required by
  *  their various anonymous descendants and pseudo-elements:
  *
  * <textarea> and <input type="text">:
  *  inherit into the XULScroll frame with class 'anonymous-div' which is a
  *  child of the text control.
  *
  * Buttons (either <button>, <input type="submit">, <input type="button">
  *          or <input type="reset">)
  *  inherit into the ':-moz-button-content' pseudo-element.
  *
  * <select>:
  *  inherit into the ':-moz-display-comboboxcontrol-frame' pseudo-element and
  *  the <optgroup>'s ':before' pseudo-element, which is where the label of
  *  the <optgroup> gets displayed. The <option>s don't use anonymous boxes,
  *  so they need no special rules.
  */
textarea > .anonymous-div,
input > .anonymous-div,
*|*::-moz-button-content,
*|*::-moz-display-comboboxcontrol-frame,
optgroup:before {
  unicode-bidi: inherit;
}
 
 /*
  * Force the text control child of file input controls to have left-to-right
  * directionality. Otherwise filenames containing right-to-left characters
  * will be reordered with chaotic results.
  */
input[type="file"] > input[type="text"] {
  direction: ltr !important;
  text-align: inherit;
}
 
@media print {
  input, textarea, select, button {
    -moz-user-input: none !important;
  }
 
  input[type="file"] { height: 2em; }
}
```**[SIZE=3]Step 6[/SIZE].** Restart Firefox
 
**Done! **:guitar:
 
[B]Screenshots:

(ugly) forms before this fix:
  [/B][IMG]http://ubuntuforums.org/attachment.php?attachmentid=92265&stc=1&d=1226457808[/IMG]

[B]forms after this fix:
[/B][IMG]http://ubuntuforums.org/attachment.php?attachmentid=92273&stc=1&d=1226460772[/IMG]
 **Notes:**
 
**Everytime Firefox updates, you will have to repeat steps 4 and 5. Just keep a copy of the fixed forms.css (ie. forms.css.dark) in your /usr/lib/xulrunner-x.x.x.x
 
**If you're using Firefox Widgets, this forms.css will stop using Firefox Widgets. However, the widgets do not use the default look, the forms.css gives them a rounded apple look.

**Swiftweasel-32 on AMD64 users: your forms.css lives in /usr/local/swiftweasel32-3/res/

---

### Post by Thingymebob on 2008-07-31
Works a treat Thanks, Might be worth making a note on how to create the stylish elements (click on icon on right of status bar > Manage styles > Write)

---

### Post by HittingSmoke on 2008-08-20
Would there be a way to convert this over to a Greasemonkey script to keep the amount of installed add-ons down?

---

### Post by RequinB4 on 2008-08-21
This is exactly what I was looking for, Thanks! -- It's not a *perfect* fix, because the addon changes the look/feel of some of the normal boxes, but it's a 20000% imporovement.

---

### Post by aparigraha on 2008-09-14
A huge THANK YOU for posting this. Really appreciated!

For people using a Swiftweasel-32bit browser on a 64-bit system, find your forms.css here:

/usr/local/swiftweasel32-3/res/forms.css

---

### Post by Zero Prime on 2008-09-24
I used this and it worked, until now.  The updated version of Firefox (3.02) doesn't seem to work right with this fix.  The buttons have black on black text and some text boxes are black on black, but not all of them.  I followed the directions on what to do after an update to no avail.

---

### Post by xandey on 2008-09-24
The firefox update changed xulrunner version, you need to modify the new version instead (step 4 above): 

```
sudo cp /usr/lib/xulrunner-1.9.0.2/res/forms.css /usr/lib/xulrunner-1.9.0.2/res/forms.css.back
```

I didn't check if step 5 should be changed or not, but it worked for me as is.

---

### Post by Zero Prime on 2008-09-25
Thanks.  Anyone ever tell you that you are the man.

I did have to change step 5 though.  Just changed the version number as in step 4 and it worked great.

Thanks again.:guitar:

---

### Post by xandey on 2008-09-26
hehe, glad it helped out. 

Turns out they modified xuirunner again today... new commands for 4 and 5:

```
sudo cp /usr/lib/xulrunner-1.9.0.3/res/forms.css /usr/lib/xulrunner-1.9.0.3/res/forms.css.back
```

```
sudo gedit /usr/lib/xulrunner-1.9.0.3/res/forms.css
```

---

### Post by laser_in_your_eye on 2008-10-19
This is great--thanks for your efforts.  One random question, though: any idea why there is a big gray box over the "Go" button at amazon.com?  The box disappears as soon as the mouse is dragged onto it.  Obviously not a deal breaker, but kind of weird.

---

### Post by bionnaki on 2008-10-20
screenshot?

---

### Post by nufros on 2008-11-11
I might have come up with a **simpler workaround using Greasemonkey**...

I don't know much about these sort of things, but if you'd care to have a look at this post ([http://ubuntuforums.org/showpost.php?p=6154407&postcount=4]("http://ubuntuforums.org/showpost.php?p=6154407&postcount=4")) detailing the same problem with before and after screenshots, you might find it a little simpler...

Or you can check out the script itself at [http://userscripts.org/scripts/show/36850]("http://userscripts.org/scripts/show/36850")

---

### Post by element_G on 2008-11-11
> **nufros said:**
> I might have come up with a simpler workaround using Greasemonkey...

I don't know much about these sort of things, but if you'd care to have a look at this post ([http://ubuntuforums.org/showpost.php?p=6154407&postcount=4](http://ubuntuforums.org/showpost.php?p=6154407&postcount=4)) detailing the same problem with before and after screenshots, you might find it a little simpler...

Or you can check out the script itself at [http://userscripts.org/scripts/show/36850](http://userscripts.org/scripts/show/36850)

It does work and it is simpler :) however, the method in this how-to does give nicer looking forms in the end

@**bionnaki**: screenshots added!

---

### Post by Ocxic on 2008-11-11
Dude this is so awesome, i could cry, I can finally see my menu's and text boxes, I could cry I'm so happy YAY!!!!!!!!

---

### Post by cstray on 2008-11-16
This is awesome!  I had to disable the "nice firefox themes" style though, because it made my radio buttons disappear (as on the poll at the top)--checkboxes too.  Kinda strange, but everything else still seems to look fine now.

---

### Post by drewster1829 on 2008-11-19
Thank you so very much!  I was so tired of not being able to see in textboxes and some buttons and menu text.   Now it works MUCH better. Thank you again!:)

---

### Post by mame58 on 2008-12-23
I want to tank you very much!! 
It's a very fine job!!

Ciao!!  :popcorn:

---

### Post by Dethv on 2008-12-24
Thank you so much, this worked great! The boxes and forms look even better than they did before.

---

### Post by JUSTINBEAIRD on 2009-02-02
does anyone know how to make a firefox feature requst like to add a preference in settings to ignore desktop layout in web pages?

Or use defalt layout in web pages option or some crap


it really needs such an option



this is one of the reasons i stayed away from dark themes even though i liked them

---

### Post by xX-Felipao-Xx on 2009-02-08
Amazing ! Thanks, really.
Use Stylish... nice idea indeed.

---

### Post by xX-Felipao-Xx on 2009-02-08
> **JUSTINBEAIRD said:**
> does anyone know how to make a firefox feature requst like to add a preference in settings to ignore desktop layout in web pages?

Or use defalt layout in web pages option or some crap


it really needs such an option



this is one of the reasons i stayed away from dark themes even though i liked them

As far as I understood... this is your solution. I mean, what dark themes have with Firefox is that the theme makes textboxs and some other things look like you put in your theme (black, grey, whatever) and that's really annoying.

For that, the guide in the first post is going to help you.

---

### Post by JUSTINBEAIRD on 2009-02-09
> **xX-Felipao-Xx said:**
> As far as I understood... this is your solution. I mean, what dark themes have with Firefox is that the theme makes textboxs and some other things look like you put in your theme (black, grey, whatever) and that's really annoying.

For that, the guide in the first post is going to help you.




yea i understand what your saying but alot of people like dark themes and i think their should be an easy solution like a checkbox in firefoxs preferences that does this autimaticly

---

### Post by parthibanbls on 2009-02-28
Worked great! Thanks a ton!

Now if I can get yelp (help-browser) to look readable with a dark theme.....

---

### Post by aparigraha on 2009-05-05
As I said earlier in the thread - Thx alot for this post! It worked great, until Firefox 3.0.10 was released. Don't now why, but now it just looks like... not usable ;) **EDIT: ** And after Firefox 3.6 things changed again... see below.

I got it working again after modifying your 2 Stylish/UserStyles scripts and at the same time merging them to only 1. It might be corrupt somehow, because I can't post it at [http://userstyles.org]("http://userstyles.org").But... IT WORKS!

If you got problems, try this:
First replace the forms.css.
The modified forms.css I use is at the bottom of this post. 
Download it and just delete the .txt ending. Replace the original with that one. 
If that doesn't work for you, try the forms.css in the first post.

After Firefox 3.6.**X**... you need to replace your forms.css file, which is located in **/usr/lib/firefox-3.6.[B]X**/res[/b]. *Where **X** is your most updated version*. Many thx to **movak** for pointing out the changed location.

Replace the forms.css through terminal:

```
sudo cp /usr/lib/firefox-3.6.**X**/res/forms.css /usr/lib/firefox-3.6.**X**/res/forms.css_backup
sudo cp /path/to/your/new/version/of/forms.css /usr/lib/firefox-3.6.**X**/res/forms.css
```

If you have an older version on Firefox (e.g. 3.0.10) replace it like this:

```
sudo cp /usr/lib/xulrunner-1.9.0.**YOUR MOST UPDATED VERSION**/res/forms.css /usr/lib/xulrunner-1.9.0.**YOUR MOST UPDATED VERSION**/res/forms.css_backup
sudo cp /path/to/your/new/version/of/forms.css /usr/lib/xulrunner-1.9.0.**YOUR MOST UPDATED VERSION**/res/forms.css

```



Then copy the code below into 'Write New Style' in Stylish/UserStyles and name it "Nice Firefox Theme and No More Dark Textboxes or Transparent Checkboxes/Radiobuttons" ;):

```
/* Set default namespace to HTML */
@namespace url(http://www.w3.org/1999/xhtml); 
@namespace xul url(http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul);
 
  /***********************  ~364  ***********************/
  /* common features of radio buttons and check boxes */
 
  input[type="radio"],
  input[type="checkbox"] {
      background-color: transparent  !important;
      border:           none         !important;
  }
 
  input[type="radio"][disabled],
  input[type="radio"][disabled]:active,
  input[type="radio"][disabled]:hover,
  input[type="radio"][disabled]:hover:active,
  input[type="checkbox"][disabled],
  input[type="checkbox"][disabled]:active,
  input[type="checkbox"][disabled]:hover,
  input[type="checkbox"][disabled]:hover:active {
      background-color: transparent  !important;
      color:            inherit      !important;
      border:           none         !important;
  }
 
  input[type="checkbox"]:focus,
  input[type="radio"]:focus {
      border-style: none  !important;
  }
 
  input[type="checkbox"]:hover:active,
  input[type="radio"]:hover:active {
      background-color:  transparent  !important;
      border-style:      none         !important;
  }
 
/*  *|*::-moz-radio {
      background-color: transparent  !important;
  }*/
 
 
 
  /* --------------------------------------------------------------------------
   *
   *    modified by phiw - Philippe Wittenbergh. phiw@l-c-n.com  emps.l-c-n.com
   *
   * -------------------------------------------------------------------------- */
 
  /*  --- Font Setting --- */
 
  html select,
  html input,
  html input[type="submit"],
  html input[type="reset"],
  html input[type="password"],
  html input[type="file"],
  html input[type="text"],
  html input:not([type]) {
      font-size: small;
  }
 
 
  /* --- Color Setting --- */
 
  html input[type="reset"],
  html input[type="submit"],
  html input[type="file"] {
      color: #1e1e1e !important; /* soft black */
  }
 
  html input,
  html textarea {
      color: #1e1e1e;
  }
 
  html button,
  html input[type="button"] {
      color: #1e1e1e !important;
  }
 
  /* --- Input, textarea  --- */
 
/*  html input,
  html input[type="text"],
  html input[type="password"],
  html textarea {
      background-color: -moz-Field;
      background-repeat: repeat-x;
      background-position: 0 0;
      -moz-border-radius: 0;
      padding: 1px 0 1px 3px;
  } */

  html input,
  html input[type="text"],
  html input[type="password"],
  html textarea {
      background-color: white !important;
      background-repeat: repeat-x;
      background-position: 0 0;
      -moz-border-radius: 0;
      padding: 1px 0 1px 3px;
  }
 
  html input,
  html textarea {
      border-top: 1px solid #616365;
      border-right: 1px solid #a0a3a5;
      border-bottom: 1px solid #bbbdbf; 
      border-left: 1px solid #616365;
  }
 
  *[dir="rtl"] input[type="text"],
  *[dir="rtl"] input[type="password"],
  *[dir="rtl"] input:not([type]),
  *[dir="rtl"] textarea {
      padding: 1px 3px 1px 0;
  }
 
  html input[type="image"] {
      border:none;
      background-image:none;
      background-color: transparent !important;
      padding:0;
  }
 
  /* --- Radio Buttons --- */
/*  *|*::-moz-radio {
      border: 0 none !important;
      background-color: transparent !important;
  }*/
 
  html input[type="radio"] {
      -moz-appearance: none;
      width: 13px !important;
      height: 13px !important;
      margin: 3px 5px 0;
      background: white no-repeat center center  !important;
/*      background: transparent no-repeat center center  !important; */
      vertical-align: baseline;
      border: 0 none !important;
      outline:none !important;
      -moz-border-radius: 0 !important;
  }
 
  html input[type="radio"]:checked {
      background: white no-repeat center center  !important;
      color: black !important;
/*      background: transparent no-repeat center center  !important; */
      border: 0 none !important;
  }
 
 
  /* --- Check Boxes --- */
 
  html input[type="checkbox"] {
      background: white no-repeat center center  !important;
      color: black !important;
      width: 13px !important;
      height:13px !important;
      margin: 1px 2px 3px 3px;
      vertical-align: text-bottom;
      -moz-border-radius: 0 !important;
      -moz-appearance: none;            /*akirasan*/
  }
 
/*  html input[type="checkbox"],
  html input[type="checkbox"]:checked{
      background: transparent no-repeat center center  !important;
      border: 0 none !important;
  } */

 
 
  html input[type="checkbox"],
  html input[type="checkbox"]:checked{
      background: white no-repeat center center  !important;
      color: black !important;
      border: 0 none !important;
  }
 
  html input[type="radio"]:focus,
  html input[type="checkbox"]:focus {
      border: 0 none !important;
  }
 



  /* --- Buttons, Submit, Reset --- */
 
  html input[type="reset"],
  html input[type="submit"],
  html input[type="file"] > input[type="button"] {
      background: #efeded repeat-x 50% 65%  !important;
      text-indent: 0 !important; /* beat those pesky ImageReplacement techniques */
      padding: 1px 4px !important;
      margin: 0;
      border: 2px solid !important;
      -moz-border-bottom-colors: #616365 #cecece;
      -moz-border-left-colors: #797b7f #fff;
      -moz-border-right-colors: #616365 #cecece;
      -moz-border-top-colors: #797b7f #fff;
      -moz-border-radius: 1px !important;
      letter-spacing:0 !important
  }
 
  html button,
  html input[type="button"],
  html button[disabled],
  html input[type="button"][disabled] { /* less strict, allows author styling */
      background: #efeded repeat-x 50% 65%;
      text-indent: 0;
      padding: 1px 4px;
      margin: 0;
      border: 2px solid;
      -moz-border-bottom-colors: #616365 #cecece;
      -moz-border-left-colors: #797b7f #e8e8e8;
      -moz-border-right-colors: #616365 #cecece;
      -moz-border-top-colors: #797b7f #e8e8e8;
      letter-spacing:0;
      -moz-border-radius: 1px;
  }
  button[disabled]:active,
  input[type="button"][disabled]:active {
      padding: 1px 4px;
      border: 2px solid;
  }
 
  /* --- input type=file --- */
 
  html input[type="file"] {
      background:transparent !important;
  }
 
  html input[type="file"] > input[type="text"] {
      margin: 0 1px 0 0;
      background-color: #fff !important;
  }
 
  html input[type="file"] > input[type="button"] {
      margin: 0 1px !important;
  }
 
  /* --- Select Options --- */
 
/*  *|*::-moz-display-comboboxcontrol-frame {
      padding: 1px 4px;
  }
 
  *|*::-moz-dropdown-list {
      border: none !important;
      border-color:transparent  !important;
      background-color: #fff !important;
  }*/
 
  html select {
      color: -moz-FieldText;
      background: #fff ;
      border: 1px solid #797b7f;
      border-color: #797b7f #999 #999 #797b7f;
      padding: 0;
      direction: ltr;
  }
  *[dir="rtl"] select,
  * select[dir="rtl"] {
      direction: rtl;
  }
 
  html select[multiple],
  html select[size],
  html select[size][multiple] {
      padding: 0;
  }
 
  html select:not([size]):not([multiple]),
  html select[size],
  html select[size="1"] {
  /*background: rgb(246, 246, 246) url("resource://gre/res/forms-grad.png") repeat-x bottom right !important;*/
      background: rgb(246, 246, 246) repeat-x bottom right  !important;
      color: #2e2e2e !important;
      height:auto !important;
      border: 2px solid !important;
      -moz-border-top-colors: #797b7f #fff;
      -moz-border-right-colors: #616365 #cecece;
      -moz-border-bottom-colors: #616365 #cecece;
      -moz-border-left-colors: #797b7f #fff;
      -moz-box-sizing: border-box !important;
      -moz-border-radius: 1px !important;
      padding:0 !important;
  }
  html select:not([size]):not([multiple]):focus,
  html select[size]:focus,
  html select[size="1"]:focus,
  html select:not([size]):not([multiple]):hover:active,
  html select[size]:hover:active,
  html select[size="1"]:hover:active {
      -moz-border-top-colors: #616365 #fff;
      -moz-border-right-colors: #797b7f #cecece;
      -moz-border-bottom-colors: #797b7f #cecece;
      -moz-border-left-colors: #616365 #fff;
  }
 
  html optgroup,
  html option {
      background:transparent;
      font-family:inherit;
      font-size:inherit;
  }
 
  html optgroup:before {
      font-style:normal;
      font-weight:normal;
      padding: 2px 5px 0 5px;
  }
  html select:not([size]):not([multiple]) optgroup:before,
  html select[size] optgroup:before,
  html select[size="1"] optgroup:before {
      color: #727272;
  }
 
  html select:not([size]):not([multiple]) option,
  html select[size] option,
  html select[size="1"] option,
  html select:not([size]):not([multiple]) optgroup,
  html select[size] optgroup,
  html select[size="1"] optgroup {
      background: transparent !important;
      color: inherit !important;
  }
  html select:not([size]):not([multiple]) option:hover,
  html select[size] option:hover,
  html select[size="1"] option:hover {
      background-color: Highlight ! important;
      color: HighlightText ! important;
  }
  html option:checked {
      background-color: Highlight ! important;
      color: HighlightText ! important;
  }
 
 
  html select > input[type="button"],
  /*html select > input[type="button"]:focus,*/
  html select > input[type="button"]:hover:active {
      background-color: transparent !important;
      background-repeat: no-repeat !important;
      background-position:  45% 50% !important;
      outline: none;
      margin: 0 !important;
      border-width: 0 2px !important;
      border-style: solid !important;
      -moz-border-left-colors: #a3a3a3 transparent !important;
      -moz-border-right-colors: transparent transparent !important;
      padding: 0 6px !important;
  }
 
  *[dir="rtl"] select > input[type="button"],
  *[dir="rtl"] select > input[type="button"]:hover:active,
  select[dir="rtl"] > input[type="button"],
  select[dir="rtl"] > input[type="button"]:hover:active {
      -moz-border-right-colors: #a3a3a3 transparent !important;
      -moz-border-left-colors: transparent transparent !important;
      background-position:  60% 50% !important;
  }
 
  /* -- focus ring - mac specific code -- maybe use outline: 1px dotted invert for Linux ? -- disabled, this reverts to the default behaviour, I think. */
 
  html input[type="reset"]:focus,
  html input[type="submit"]:focus {
      color:#262626 !important;
  }
 
  /* --- disabled widgets --- */
 
 
  html input[type="reset"][disabled],
  html input[type="submit"][disabled],
  html input[type="file"][disabled],
  html select[disabled],
  html select[disabled] option,
  html option[disabled] {
      color:#727272 !important;
  }
  html input[disabled],
  html textarea[disabled],
  html option[disabled],
  html optgroup[disabled],
  html select[disabled],
  html select[disabled]>* {
      -moz-user-input: disabled;
      -moz-user-focus: ignore;
  }
 
  html select[disabled] > input[type="button"] {
      border:none;
      border-left:2px solid;
      -moz-border-left-colors: #b3b3b3 transparent;
  }
 
  html option[disabled],
  html optgroup[disabled] {
      background-color: transparent;
  }
 
  html input[type="radio"][disabled],
  html input[type="radio"][disabled]:active,
  html input[type="radio"][disabled]:hover,
  html input[type="radio"][disabled]:hover:active,
  html input[type="checkbox"][disabled],
  html input[type="checkbox"][disabled]:active,
  html input[type="checkbox"][disabled]:hover,
  html input[type="checkbox"][disabled]:hover:active {
      border: 0 none !important;
      background-color: transparent !important;
      outline-width: 0 !important;
  }
 
  html select[disabled],
  html input[disabled],
  html textarea[disabled],
  html button[disabled],
  html input[type="checkbox"][disabled],
  html input[type="radio"][disabled],
  html input[type="button"][disabled],
  html input[type="reset"][disabled],
  html input[type="submit"][disabled] {
      opacity: 0.6;
  }
 
  html input[type="file"][disabled] > * {
      opacity:1.0 !important;
  }
 
 
 
  /****************************************************************************\
    :CHANGES: void
  \****************************************************************************/
 
  input[type="file"] > input[type="text"],
  html input:not([type]),
  html input[type="text"],
  html input[type="password"],
  html textarea {
      -moz-border-radius: 3px;
  }
 
  /**
   *  BASE 64 IMAGES
   */
  html input,
  html input[type="text"],
  html input[type="password"],
  html textarea {
      background-image: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAQAAAAECAYAAACp8Z5+AAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEgAACxIB0t1+/AAAABV0RVh0Q3JlYXRpb24gVGltZQAwNC45LjE4xKRlPwAAACF0RVh0U29mdHdhcmUATWFjcm9tZWRpYSBGaXJld29ya3MgNC4w6iYndQAAACJJREFUeJxjXLxk2WYGJMDCwMDQiyzA+P//f2Q+AxMDGgAAJwEGM2kcXr8AAAAASUVORK5CYII=");
  }
  html input[type="radio"] {
      background-image: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAA0AAAANCAYAAABy6+R8AAAABGdBTUEAANbY1E9YMgAAABl0RVh0U29mdHdhcmUAQWRvYmUgSW1hZ2VSZWFkeXHJZTwAAAG9SURBVCjPfZLLaiJBFIYrBHyK7GYZHPIAWc4ziCIYRFy4cKOgYCO46IUuFDR4GUTTm8aF4kaia0FFwY1CIl5oFFva0YwGaTD2JWdOCQFJ4hR8FFWn/lOnzl8EAMgHJpPJaDabi1arVbTZbGC320Wn01l0uVzG03Mfhw0IY7FYlHA4PG+1WvJwOIR2uy0nEgnR7XYrHo+H8fl8l6eie8y86fV6qqZp8JnBYKAGAoG/DMPcH0UouMWStEaj8YYDztHtdt9CoZDGsuwtQQHv9/ufMRvIsnwWGk+lUk+RSIQn9NE8z79g/dDv90EURViv17DZbI4zXdN9Gq9UKi/RaFQk+JZDvV5XaSbKZDL5lvF4DJ1OR43H4wficDikarW6nU6nMJvNQJKkL9B9Gm82m9t0Ov2HeL3ex1gsJqxWK9jtdmeh8XK5LHAc90geOO6O+jAajf7bvcVioWUyGaVQKPwie0X/GQwGC8gWa9dxwGfm87mey+W22Wz299GnvfJuxCw/0DgWfdBLpdIrFS+XSxAEQa/Vaq94g44CNp/PG46iw169RtevcHGBxt2gD0Vsq4RdgmQyKaGgiIKb07/3DxehBztkriL/AAAAAElFTkSuQmCC")  !important;
  }
  html input[type="radio"]:checked {
      background-image: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAA0AAAANCAYAAABy6+R8AAAABGdBTUEAANlkkQC7WgAAACBjSFJN    AAB5FwAAgOgAAOvlAACGZQAAgC4AAN3gAAA5EwAALfFDOSc6AAAACXBIWXMAAAsTAAALEwEAmpwYAAABx0lEQVQoz31SOWsCURB+BNbC3xFSp9RGGzvriCAICoImneAWaqULshALC8HEAwQjJForsTCFCBtZzCLieuGBFh6YwlgIKpN5SxI0kDz4ePtm5pvjmyUAQL5hMpnOzWYzb7FYClarVbTZbAWHw8G7XK7z47jvYAZhx0ApFov16vX6x3A4BEmSPtLpdN/tdksIO8uyZ8ckFrNJnU5nt9/v4TcGg8EuEAi8+Xw+ViEh4RLbkURR3OKBv9BoNLZIlDiOuyQ4AxcMBl9lWYbNZgPdbheMRiOoVCrlpm9qp/5UKiXwPM8ROnQ+n18KgkCzgU6nw/rkBxqNRrFTf7FYXIbD4QJBhWrVanVHM1Go1eoTEsMw0O/3odfrAY6wi0QiAnE6nS/lcvl9NBrBeDwGvV5/QtJqtYqd+mu12nsikagQr9d7jx/NxWIB6/UaWq0WGAwGhUBv+qZ26sf2mpmHzB15fHq68ng8TdzLv+rN5/N9Mpls5nI5rbInlPEWVZEnk8kBD/zGbDY7ZLNZGTvy/SyXwu/334RCoXapVFpS8mq1gul0eqhUKkus0I7H49coOXNC+qp4gRV5lPUZVRKj0egz/lY8Ei6O4z4Bnd/QpvegPQoAAAAASUVORK5CYII=")  !important;
  }
  html input[type="checkbox"],
  html input[type="checkbox"]:checked{
      background-image: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAA0AAAANCAYAAABy6+R8AAAABGdBTUEAANbY1E9YMgAAABl0RVh0U29mdHdhcmUAQWRvYmUgSW1hZ2VSZWFkeXHJZTwAAAE6SURBVCjPhZI9bipBEISremYX9g82sHPkKzglQYgrcIF3Bl/ByTuUJRLA+BgkpMgae0fTPY6QLNmYlkodfWr1p+J6va4BPAFYkGxFBN/jnLvkXURenHP/PYCn1Wr1b7lc3vd9P8aVOZ/Pn/v9/mG328EDWMzn87vZbDbOOV9j0Pf9OMZ4dzgcFp5kN51Oq5QS/oJIom3byjnXeTOjqkJVQfJXkCTMDKoKM6MnyZQShmGAiFy9ZGZIKQEAPUmEEBBCgHPuKqSqAAARgW+aRoqiAMmbUM4ZdV2L77pOyrJEWZY3oRgjqqoSP5lMfFVV8N7f/Mk5h6ZpvG/bdsg5p9FoJCIif9izlJLVdT1IURSvx+PxQ1Xzt8r8iJnl0+n0ISKvPsb4vNlsuu12+0iyuRi67IsgkkFV30IIz18cwI1NeExqHQAAAABJRU5ErkJggg==")  !important;
  }
  html input[type="reset"],
  html input[type="submit"],
  html input[type="file"] > input[type="button"] {
      background-image: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAoAAAA8CAYAAABfESsNAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEgAACxIB0t1+/AAAABZ0RVh0Q3JlYXRpb24gVGltZQAwNS4xMS4yN6/1yKEAAAAhdEVYdFNvZnR3YXJlAE1hY3JvbWVkaWEgRmlyZXdvcmtzIDQuMOomJ3UAAABhSURBVHic7dPBCYAwDEZhW1xCwZS6/1JqelYHCHEC5R0EEfKfP94hkOTuYweWCQoYMGDAgPfr9+NkcFGFcGvfFSFctTmB/I61TAzOIi8Xa6FFYcVkZgMq5swu9IdXCPi4C6HeHFixIGPzAAAAAElFTkSuQmCC")  !important;
  }
 
  html input[type="reset"]:focus,
  html input[type="submit"]:focus,
  html input[type="reset"]:hover,
  html input[type="submit"]:hover,
  html input[type="reset"]:hover:active,
  html input[type="submit"]:hover:active {
      background-image: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAoAAAA8CAYAAABfESsNAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEgAACxIB0t1+/AAAABZ0RVh0Q3JlYXRpb24gVGltZQAwNS4xMS4yN6/1yKEAAAAhdEVYdFNvZnR3YXJlAE1hY3JvbWVkaWEgRmlyZXdvcmtzIDQuMOomJ3UAAABjSURBVHic7dPBCYBADERRN9iEu7CWov23oWL2JnoOsQLl30TInB8ZGEhy97kDEYICBgwYMOBz+uO8GFx3pbBBqBTS6oVWb9qcQL5jLQODY4awlvxRdTKzCV0UYQv94RUCvuYGx8ocsZqoiv8AAAAASUVORK5CYII=")  !important;
  }
 
  html button,
  html input[type="button"],
  html button[disabled],
  html input[type="button"][disabled] { /* less strict, allows author styling */
      background-image: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAoAAAA8CAYAAABfESsNAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEgAACxIB0t1+/AAAABZ0RVh0Q3JlYXRpb24gVGltZQAwNS4xMS4yN6/1yKEAAAAhdEVYdFNvZnR3YXJlAE1hY3JvbWVkaWEgRmlyZXdvcmtzIDQuMOomJ3UAAABhSURBVHic7dPBCYAwDEZhW1xCwZS6/1JqelYHCHEC5R0EEfKfP94hkOTuYweWCQoYMGDAgPfr9+NkcFGFcGvfFSFctTmB/I61TAzOIi8Xa6FFYcVkZgMq5swu9IdXCPi4C6HeHFixIGPzAAAAAElFTkSuQmCC");
  }
  html button:focus,
  html input[type="button"]:focus,
  html button:hover,
  html input[type="button"]:hover,
  html button:hover:active,
  html input[type="button"]:hover:active {
      background-image: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAoAAAA8CAYAAABfESsNAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEgAACxIB0t1+/AAAABZ0RVh0Q3JlYXRpb24gVGltZQAwNS4xMS4yN6/1yKEAAAAhdEVYdFNvZnR3YXJlAE1hY3JvbWVkaWEgRmlyZXdvcmtzIDQuMOomJ3UAAABjSURBVHic7dPBCYBADERRN9iEu7CWov23oWL2JnoOsQLl30TInB8ZGEhy97kDEYICBgwYMOBz+uO8GFx3pbBBqBTS6oVWb9qcQL5jLQODY4awlvxRdTKzCV0UYQv94RUCvuYGx8ocsZqoiv8AAAAASUVORK5CYII=");
  }
  html select:not([size]):not([multiple]),
  html select[size],
  html select[size="1"] {
      background-image: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAARCAYAAAAcw8YSAAAABGdBTUEAANbY1E9YMgAAABl0RVh0U29mdHdhcmUAQWRvYmUgSW1hZ2VSZWFkeXHJZTwAAABZSURBVHjaYvr//z8DQAAxMQIBQAAxMTAwMAIEEIhgAgggMAsggMAEQACBuQABBCYAAgjMBQggMAsggMAsgAACswACCMwCCCAwCyCAwCyAAAITAAEEJgACDAACqAM55WzqjgAAAABJRU5ErkJggg==")  !important;
  }
  html select > input[type="button"],
  /*html select > input[type="button"]:focus,*/
  html select > input[type="button"]:hover:active {
      background-image: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABMAAAAZCAYAAADTyxWqAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAAK8AAACvABQqw0mAAAACF0RVh0U29mdHdhcmUATWFjcm9tZWRpYSBGaXJld29ya3MgNC4w6iYndQAAALdJREFUeJzt1E0KgzAQhuHXaqEV3HSVg8z9TzBXEXHTH6ykmxSETkZbsii0szMZH744ahVjpFTtikl/7KNq1hpEpAZqYFbV2et1kyWoA25Al67fxxbQkJaGNdDEDOhZLphLVhvQEjQxbwAnYG+sT7kbqpLfpplMRBqgJZ/srKr3TVhCRidEC7xguQFMQMjsBTLPzcTSEXoDDEBvHdFLZoEuBBumKSIH4AhcVPXq9RZ9Nb73f/Yj2AOpzz2UFWQSawAAAABJRU5ErkJggg==")  !important;
  }
```

Hope it helps someone.
/aparigraha

---

### Post by element_G on 2009-05-05
thanks for the update, I have edited the OP :KS

---

### Post by zurih on 2009-05-08
Hi everyone,

Somehow I lost my backup forms.css file and I want to get back as it was before.

Anyone has the backup forms.css file and can deliver it to me somehow?

Would really appreciate it.

Thanks

---

### Post by element_G on 2009-05-08
Here is my forms.css (just need to rename it as .css instead of .txt)

---

### Post by zurih on 2009-05-09
> **element_G said:**
> Here is my forms.css (just need to rename it as .css instead of .txt)

Thank you so much! :KS

---

### Post by drewster1829 on 2009-05-17
Thanks, aparigraha!  I was getting tired of not having any buttons on dialog boxes.  Your solution works great for the new version of firefox. ;)

---

### Post by overridex on 2009-06-16
Argh, this had been working beautifully until the upgrade to Firefox 3.0.11 yesterday - back to my ugly buttons. :(

---

### Post by aparigraha on 2009-06-18
@overridex

Just replace the forms.css with the one in [this]("http://ubuntuforums.org/showpost.php?p=7220196&postcount=24") post and 3.0.11 will hopefully look nice again. Remember to backup the file first though :)

---

### Post by overridex on 2009-06-25
Thanks aparigraha.

---

### Post by mjrmua on 2009-08-20
This fix sorts out my HTML form elements, but I'm still getting black text on a black background in firefox's location and search bars. 

Any ideas?

---

### Post by bagy on 2009-09-08
Tnx...:)))

---

### Post by bagy on 2009-09-09
Thank you man....GREAT...:)))

---

### Post by asgard_command on 2009-11-18
Still love this fix. But is there no way to stop it making the 'go' and 'add to basket' buttons on Amazon disappear.

---

### Post by Tamale on 2009-11-25
thank you!! this works great.. but it's really sad they haven't sorted out this bug between the firefox and GTK developers automatically!!

there's no reason for GTK themes to screw with firefox's form elements.. it's a browser meant to view any kind of page, not an element of the desktop environment!

---

### Post by sigurnjak on 2009-11-25
Here is a theme i have been tweaking for a while to look the way i like .
It may not be as dark as some would like to , but i feel it strikes nice balance  and firefox looks good .

---

### Post by movak on 2010-01-06
> **asgard_command said:**
> But is there no way to stop it making the 'go' and 'add to basket' buttons on Amazon disappear.

There is one! Search in your user style for "image" and add the bold line to the definitions:

  ```
html input[type="image"] {
      border:none;
      background-image:none;
**      background-color: transparent !important;**
      padding:0;
  }
```This works for me using aparigraha's forms.css and style.

---

### Post by asgard_command on 2010-01-07
This edit made my white box disappear but left a blank space still instead of the button image. Mabye I use a different style might try starting from scratch again.

---

### Post by movak on 2010-01-07
That's actually very strange! I can easily explain why you previously saw a white box. But I have no clue which style rule(s) (in combination with the new rule) could possibly produce the outcome you described. And I've dealt with this issue for quite a while! :D So I'm curious if you can get it work with the untouched style code from aparigraha.  Btw, don't forget the userContent.css!

---

### Post by aparigraha on 2010-01-17
I updated my earlier [post]("http://ubuntuforums.org/showpost.php?p=7220196&postcount=24") to contain:

```
html input[type="image"] {
      border:none;
      background-image:none;
      **background-color: transparent !important;**
      padding:0;
  }
```


Although it didn't help me much, it might help someone. Might depend on ones location. I have and have always had a "Go"-button and instead of a "Add to Basket"-button I have and have always had a "Add to Cart"-button. If I go to [http://www.amazon.co.uk]("http://www.amazon.co.uk"), I get a Go-, and a Basket-button with and without [my posted script]("http://ubuntuforums.org/showpost.php?p=7220196&postcount=24").

Why you don't I do not know.

---

### Post by asgard_command on 2010-01-18
Started from scratch and the new code fixed all my problems. Not sure which version of style and forms.css I had before but all good now.

Thanks for the work on this.

---

### Post by YosefKaro on 2010-01-24
Actually, this fix worked just fine for me right up to firefox 3.6 and now it is no longer working.  I would try the second post that is mentioned above but I cannot understand his instructions.  Please let me know when a fix becomes available for this.

-Yos

---

### Post by undoIT on 2010-01-25
Is there any way to implement this so that forms.css doesn't need to be edited every time xulrunner is updated?

---

### Post by movak on 2010-01-30
@YosefKaro

I've just tested it with Swiftfox 3.6 and it worked fine. What exactly don't you understand in the instructions? You actually just have to replace the forms.css in the res-directory with that from aparigraha and add the user style to Stylish.

---

### Post by anihilat0r on 2010-01-31
YosefKaro is right, it just doesn't work in 3.6. The Stylish script seems OK (tried both, from the OP and the one from aparigraha), but the forms.css does not convert the buttons, they are still all black.

---

### Post by movak on 2010-02-01
Hm, strange. I've now also tested it with the official tarball from mozilla.org and still have no problems.. How did you guys install the new version?

---

### Post by anihilat0r on 2010-02-01
> **movak said:**
> Hm, strange. I've now also tested it with the official tarball from mozilla.org and still have no problems.. How did you guys install the new version?

That's odd... Anyway, I installed it by adding 
*deb [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu) karmic  main*
to my sources.list, purging the old FF (3.5 from the official ubuntu repositories) and re-installing.

I have xulrunner-1.9.0.14 and -1.9.1.7 installed if that is any help..

---

### Post by movak on 2010-02-01
Ok, I installed Firefox 3.6 from the stable PPA and still have no problems :)

However, the forms.css is stored with this version in a different directory. It's in /usr/lib/firefox-3.6/res. So if you replace it there it should  work again.

---

### Post by anihilat0r on 2010-02-01
It works now! Thank You, you're a lifesaver!

---

### Post by movak on 2010-02-01
Glad to hear that :)

---

### Post by undoIT on 2010-03-31
> **movak said:**
> Ok, I installed Firefox 3.6 from the stable PPA and still have no problems :)

However, the forms.css is stored with this version in a different directory. It's in /usr/lib/firefox-3.6/res. So if you replace it there it should  work again.

Thanks! This was the key to getting it working in Firefox 3.6 for me :)

---

### Post by kaotik2003 on 2010-05-30
> **movak said:**
> Ok, I installed Firefox 3.6 from the stable PPA and still have no problems :)

However, the forms.css is stored with this version in a different directory. It's in /usr/lib/firefox-3.6/res. So if you replace it there it should  work again.


Thanks, t worked perfectly on my 3.6.3

---

### Post by Markkreuzz on 2010-06-03
Im using 8.04 Hardy and works on firefox 3.0.19. But when i upgraded to ubuntuzilla's ppa **3.6.3** it didnt work. I tried looking for /usr/lib/firefox-3.6/res/forms.css and it aint there. i have a /firefox, /mozilla, /mozilla-firefox folder and theyre not there either :(

**[COLOR="Red"]Update:[/COLOR]**

I finally got it working!!!:shock: I removed ubuntuzilla's ppa and its version of 3.6 and replaced it with mozillateams PPA!!!! I believe the problem could be that ubuntuzilla's version uses a different /res folder. The mozillateams version has the /usr/lib/firefox-3.6/res/ which contains the forms.css file that needs to be modified ](*,). Anyways im a happy camper now. *cheers*

---

### Post by mdonahoe on 2010-07-05
This worked great for me and thank you very very much.  One of the persons replying had asked about how to submit a request to mozilla, wondering if anyone had done that yet.  This whole issue seems like it would be something Mozilla would want corrected from a user experience standpoint and would be simple.  

I know if Chromium had a few of the 'essential' add ons available that I love in firefox it would be a simple and easy switch for me.  Chromium just looks amazing and trouble free with the dark backgrounds..

Anyway thanks for the fix!:P

---

### Post by htexmexh on 2010-07-18
Many thanks for this fix, I made a new account just to thank you, because NOTHING else has ever worked, EVER, except this :D

This makes me really happy, because it was really pissing me off.

---

### Post by th3 on 2010-07-26
thanks you very much friends, especially element_G.

---

### Post by wcradar on 2010-07-27
I am having Pitch Dark 3.0.2 also.. i have never changed my theme from the time i installed, its really nice one

---

### Post by smoosh on 2010-08-02
Bellisimo! Thanks!

---

### Post by movak on 2010-08-08
I wrote a little script that replaces the forms.css after a Firefox update. You can download it in the [corresponding thread]("http://ubuntuforums.org/showthread.php?t=1546538") where you also can post if you have any problems with it.

---

### Post by movak on 2010-09-18
The [dark themes bug]("https://bugzilla.mozilla.org/show_bug.cgi?id=519763") is now recorded in Bugzilla but hasn't been assigned to anyone yet. There are currently only 2 votes for it. Furthermore, the priority for this bug is probably not very high as it only concerns Linux platforms. If you want to vote for it you just have to enter an Email address to [create an account]("https://bugzilla.mozilla.org/createaccount.cgi"). Maybe this will increase the bug importance somewhat..

---

### Post by anathema415 on 2010-12-31
Everything worked great here except that my address bar at the top is still white on white text. Any suggestions?

---

### Post by movak on 2011-01-01
The steps in this HowTo only change the appearance of web pages. So this is most likely a problem of your Qt/GTK-Theme. You can try to adjust the colors of entry fields in [I]Administration / Preferences / Appearance / Customize.. / Colors
[/I]

---

### Post by lufte on 2011-03-24
What's the deal with firefox 4?

---

### Post by bagy on 2011-03-25
Now we have problem with firefox 4 and dark themes...

EDIT: Fixed [http://ubuntuforums.org/showthread.php?t=1715031&highlight=firefox+dark+themes](http://ubuntuforums.org/showthread.php?t=1715031&highlight=firefox+dark+themes)

---

