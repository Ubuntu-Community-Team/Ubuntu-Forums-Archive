---
title: "CSS/HTML question - heading span 100% of width"
date: 2010-06-14
forum: Programming Talk
---

### Post by cdaringe on 2010-06-14
hi all:

perhaps this is not the best forum to be posting this in--let me know if you think there is a more fitting location.

been doin' html for a while, but my css is rusty :/  I'm throwing together a site, but can't get a banner to render properly.  at my personal site, [www.chrisdieringer.net](www.chrisdieringer.net), youll see a dark green bar that runs the length of the screen (says "HOME" in it at the homepage).  That is currently the h1 element.  I'm trying to duplicate the effect on this other site, [www.ceeznet.net](www.ceeznet.net) .  Need some pointers/ideas.

Attached is the .php file that has the html in it and the css file.  Any tips would be awesome!

-Chris

css:
```

/* $Id: style.css,v 1.23 2007/12/17 15:05:09 goba Exp $ */

/*
** HTML elements
*/
body {
  margin-top:15px;
  margin-bottom:15px;
  padding: 0;
  background-color: #E1ECE1;
  margin-left:auto;
  margin-right:auto;
  font-size: 11px;
  font-family: Verdana, Arial, SunSans-Regular, Sans-Serif;
  color:#003300;
  /* margin:0; */
}
tr.odd td, tr.even td {
  padding: 0.3em;
}

h1, h2, h3, h4, h5, h6 {
  margin-bottom: 0.5em;
}
h1 {
  font-size: 1.3em;
}
h2 {
  font-size: 1.2em;
}
h3, h4, h5, h6 {
  font-size: 1.1em;
}
h7 {
font-size: 10px;
text-transform:uppercase;
background-color:#669966;
border-top:1px solid #564b47;
border-bottom:1px solid #564b47;
padding:2px 6px;
margin:0;
width: 100%; ! important
}

p {
  margin-top: 0.5em;
  margin-bottom: 0.9em;
}
a {
  text-decoration: none;
  /* font-weight: bold; */
}
a:link {
  color: #000099;
}
a:visited {
  color: #336699;
}
a:hover {
  color: #00004D;
  text-decoration: underline;
}
fieldset {
  border: 1px solid #ccc;
}
pre {
  background-color: #eee;
  padding: 0.75em 1.5em;
  font-size: 12px;
  border: 1px solid #ddd;
}
table {
  /* make <td> sizes relative to body size! */
  font-size: 1em;
  margin-left:auto;
  margin-right:auto;
}
.form-item label {
  font-size: 1em;
  color: #002400;
}
.item-list .title {
  font-size: 1em;
  color: #002400;
}
.links {
  margin-bottom: 0;
}
.comment .links {
  margin-bottom: 0;
}

/*
** Page layout blocks / IDs
*/
#header, #content {
  width: 95%;
}
#header {
  background-color: #a8c79d;
  margin-left:auto;
  margin-right:auto;
  padding:0px 0px; 
}

#logo {
  vertical-align: middle;
  width:100%;
  margin-right:0px;
  padding:0px 0px; 
  border: 0;
}
#logo img {
  float: right; /* LTR */
  border: 0;
  padding:0px 0px; 
}
#menu {
  padding: 0.0em 0.0em 0 0.0em; /* LTR */
  text-align: right; /* LTR */
  vertical-align: middle;
}
#navlist {
  font-size: 1.0em;
  padding: 0 0.8em 1.2em 0; /* LTR */
  color: #9cf;
}
#navlist a {
  font-weight: bold;
  color: #fff;
}
#subnavlist {
  padding: 0.5em 1.2em 0.4em 0; /* LTR */
  font-size: 0.8em;
  color: #9cf;
}
#subnavlist a {
  font-weight: bold;
  color: #9cf;
}
ul.links li {
  border-left: 1px solid #9cf; /* LTR */
}
ul.links li.first {
  border: none;
}
#search .form-text, #search .form-submit {
  border: 1px solid #369;
  font-size: 1.1em;
  height: 1.5em;
  vertical-align: middle;
}
#search .form-text {
  width: 8em;
  padding: 0 0.5em;
}
#mission {
  background-color: #369;
  padding: 1.5em 2em;
  color: #fff;
}
#mission a, #mission a:visited {
  color: #9cf;
  font-weight: bold;
}
.site-name {
  margin: 0.6em 0 0 ;
  padding: 0;
  font-size: 2em;
}
.site-name a:link, .site-name a:visited {
  color: #fff;
}
.site-name a:hover {
  color: #369;
  text-decoration: none;
}
.site-slogan {
  font-size: 1em;
  color: #eee;
  display: block;
  margin: 0;
  font-style: italic;
  font-weight: bold;
}
#main {
  /* padding in px not ex because IE messes up 100% width tables otherwise */
  padding: 10px;
}
#mission, .node .content, .comment .content {
  line-height: 1.4em;
}
#help {
  font-size: 0.9em;
  margin-bottom: 1em;
}
.breadcrumb {
  margin-bottom: .5em;
}
.messages {
  background-color: #eee;
  border: 1px solid #ccc;
  padding: 0.3em;
  margin-bottom: 1em;
}
.error {
  border-color: red;
}
#sidebar-left{
  background-color: #7ab469;
  width: 16em;
  /* padding in px not ex because IE messes up 100% width tables otherwise */
  padding: 10px;
  vertical-align: top;
}

#sidebar-right {
  background-color: #bfd788;
  width: 16em;
  /* padding in px not ex because IE messes up 100% width tables otherwise */
  padding: 10px;
  vertical-align: top;

bfd788;
}

#footer {
  background-color: #669966;
  padding: 5px -2px;
  margin-left:auto;
  margin-right:auto;
  font-size: 0.8em;
  width: 95%;
}

/*
** Common declarations for child classes of node, comment, block, box, etc.
** If you want any of them styled differently for a specific parent, add
** additional rules /with only the differing properties!/ to .parent .class.
** See .comment .title for an example.
*/
.title, .title a {
  font-weight: bold;
  font-size: 1.3em;
  color: #002400;
  margin: 0 auto;  /* decrease default margins for h<x>.title */
}
.submitted {
  color: #999;
  font-size: 0.8em;
}
.links {
  color: #999;
}
.links a {
  font-weight: bold;
}
.block, .box {
  padding: 0 0 1.5em 0; /* LTR */
}
.block {
  border-bottom: 1px solid #bbb;
  padding-bottom: 0.75em;
  margin-bottom: 1.5em;
}
.block .title {
  margin-bottom: .25em;
}
.box .title {
  font-size: 1.1em;
}
.node {
  margin: .5em 0 2em; /* LTR */
}
.sticky {
  padding: .5em;
  background-color: #eee;
  border: solid 1px #ddd;
}
.node .content, .comment .content {
  margin: .5em 0 .5em;
}
.node .taxonomy {
  color: #999;
  font-size: 0.8em;
  padding-left: 1.5em; /* LTR */
}
.node .picture {
  border: 1px solid #ddd;
  float: right; /* LTR */
  margin: 0.5em;
}
.comment {
  border: 1px solid #abc;
  padding: .5em;
  margin-bottom: 1em;
}
.comment .title a {
  font-size: 1.1em;
  font-weight: normal;
}
.comment .new {
  text-align: right; /* LTR */
  font-weight: bold;
  font-size: 0.8em;
  float: right; /* LTR */
  color: red;
}
.comment .picture {
  border: 1px solid #abc;
  float: right; /* LTR */
  margin: 0.5em;
}

/*
** Module specific styles
*/
#aggregator .feed-source {
  background-color: #eee;
  border: 1px solid #ccc;
  padding: 1em;
  margin: 1em 0;
}
#aggregator .news-item .categories, #aggregator .source, #aggregator .age {
  color: #999;
  font-style: italic;
  font-size: 0.9em;
}
#aggregator .title {
  margin-bottom: 0.5em;
  font-size: 1em;
}
#aggregator h3 {
  margin-top: 1em;
}
#forum table {
  width: 100%;
}
#forum td {
  padding: 0.5em;
}
#forum td.forum, #forum td.posts {
  background-color: #eee;
}
#forum td.topics, #forum td.last-reply {
  background-color: #ddd;
}
#forum td.container {
  background-color: #ccc;
}
#forum td.container a {
  color: #555;
}
#forum td.statistics, #forum td.settings, #forum td.pager {
  height: 1.5em;
  border: 1px solid #bbb;
}
#forum td .name {
  color: #96c;
}
#forum td .links {
  padding-top: 0.7em;
  font-size: 0.9em;
}
#profile .profile {
  clear: both;
  border: 1px solid #abc;
  padding: .5em;
  margin: 1em 0em;
}
#profile .profile .name {
  padding-bottom: 0.5em;
}
.block-forum h3 {
  margin-bottom: .5em;
}
div.admin-panel .description {
  color: #999;
}
div.admin-panel .body {
  background: #f4f4f4;
}
div.admin-panel h3 {
  background-color: #69c;
  color: #fff;
  padding: 5px 8px 5px;
  margin: 0;
}
/* $Id: style.css,v 1.23 2007/12/17 15:05:09 goba Exp $ */

/*
** HTML elements
*/
body {
  margin-top:15px;
  margin-bottom:15px;
  padding: 0;
  background-color: #E1ECE1;
  margin-left:auto;
  margin-right:auto;
  font-size: 11px;
  font-family: Verdana, Arial, SunSans-Regular, Sans-Serif;
  color:#003300;
  /* margin:0; */
}
tr.odd td, tr.even td {
  padding: 0.3em;
}

h1, h2, h3, h4, h5, h6 {
  margin-bottom: 0.5em;
}
h1 {
  font-size: 1.3em;
}
h2 {
  font-size: 1.2em;
}
h3, h4, h5, h6 {
  font-size: 1.1em;
}
/* h7 {
font-size: 10px;
text-transform:uppercase;
background-color:#669966;
border-top:1px solid #564b47;
border-bottom:1px solid #564b47;
padding:2px 6px;
margin:0 } */
p {
  margin-top: 0.5em;
  margin-bottom: 0.9em;
}
a {
  text-decoration: none;
  /* font-weight: bold; */
}
a:link {
  color: #000099;
}
a:visited {
  color: #336699;
}
a:hover {
  color: #00004D;
  text-decoration: underline;
}
fieldset {
  border: 1px solid #ccc;
}
pre {
  background-color: #eee;
  padding: 0.75em 1.5em;
  font-size: 12px;
  border: 1px solid #ddd;
}
table {
  /* make <td> sizes relative to body size! */
  font-size: 1em;
  margin-left:auto;
  margin-right:auto;
}
.form-item label {
  font-size: 1em;
  color: #002400;
}
.item-list .title {
  font-size: 1em;
  color: #002400;
}
.links {
  margin-bottom: 0;
}
.comment .links {
  margin-bottom: 0;
}

/*
** Page layout blocks / IDs
*/
#header, #content {
  width: 95%;
}
#header {
  background-color: #a8c79d;
  margin-left:auto;
  margin-right:auto;
  padding:0px 0px; 
}

#logo {
  vertical-align: middle;
  width:100%;
  margin-right:0px;
  padding:0px 0px; 
  border: 0;
}
#logo img {
  float: right; /* LTR */
  border: 0;
  padding:0px 0px; 
}
#menu {
  padding: 0.0em 0.0em 0 0.0em; /* LTR */
  text-align: right; /* LTR */
  vertical-align: middle;
}
#navlist {
  font-size: 1.0em;
  padding: 0 0.8em 1.2em 0; /* LTR */
  color: #9cf;
}
#navlist a {
  font-weight: bold;
  color: #fff;
}
#subnavlist {
  padding: 0.5em 1.2em 0.4em 0; /* LTR */
  font-size: 0.8em;
  color: #9cf;
}
#subnavlist a {
  font-weight: bold;
  color: #9cf;
}
ul.links li {
  border-left: 1px solid #9cf; /* LTR */
}
ul.links li.first {
  border: none;
}
#search .form-text, #search .form-submit {
  border: 1px solid #369;
  font-size: 1.1em;
  height: 1.5em;
  vertical-align: middle;
}
#search .form-text {
  width: 8em;
  padding: 0 0.5em;
}
#mission {
  background-color: #369;
  padding: 1.5em 2em;
  color: #fff;
}
#mission a, #mission a:visited {
  color: #9cf;
  font-weight: bold;
}
.site-name {
  margin: 0.6em 0 0 ;
  padding: 0;
  font-size: 2em;
}
.site-name a:link, .site-name a:visited {
  color: #fff;
}
.site-name a:hover {
  color: #369;
  text-decoration: none;
}
.site-slogan {
  font-size: 1em;
  color: #eee;
  display: block;
  margin: 0;
  font-style: italic;
  font-weight: bold;
}
#main {
  /* padding in px not ex because IE messes up 100% width tables otherwise */
  padding: 10px;
}
#mission, .node .content, .comment .content {
  line-height: 1.4em;
}
#help {
  font-size: 0.9em;
  margin-bottom: 1em;
}
.breadcrumb {
  margin-bottom: .5em;
}
.messages {
  background-color: #eee;
  border: 1px solid #ccc;
  padding: 0.3em;
  margin-bottom: 1em;
}
.error {
  border-color: red;
}
#sidebar-left{
  background-color: #7ab469;
  width: 16em;
  /* padding in px not ex because IE messes up 100% width tables otherwise */
  padding: 10px;
  vertical-align: top;
}

#sidebar-right {
  background-color: #bfd788;
  width: 16em;
  /* padding in px not ex because IE messes up 100% width tables otherwise */
  padding: 10px;
  vertical-align: top;

bfd788;
}

#footer {
  background-color: #669966;
  padding: 5px -2px;
  margin-left:auto;
  margin-right:auto;
  font-size: 0.8em;
  width: 95%;
}

/*
** Common declarations for child classes of node, comment, block, box, etc.
** If you want any of them styled differently for a specific parent, add
** additional rules /with only the differing properties!/ to .parent .class.
** See .comment .title for an example.
*/
.title, .title a {
  font-weight: bold;
  font-size: 1.3em;
  color: #002400;
  margin: 0 auto;  /* decrease default margins for h<x>.title */
}
.submitted {
  color: #999;
  font-size: 0.8em;
}
.links {
  color: #999;
}
.links a {
  font-weight: bold;
}
.block, .box {
  padding: 0 0 1.5em 0; /* LTR */
}
.block {
  border-bottom: 1px solid #bbb;
  padding-bottom: 0.75em;
  margin-bottom: 1.5em;
}
.block .title {
  margin-bottom: .25em;
}
.box .title {
  font-size: 1.1em;
}
.node {
  margin: .5em 0 2em; /* LTR */
}
.sticky {
  padding: .5em;
  background-color: #eee;
  border: solid 1px #ddd;
}
.node .content, .comment .content {
  margin: .5em 0 .5em;
}
.node .taxonomy {
  color: #999;
  font-size: 0.8em;
  padding-left: 1.5em; /* LTR */
}
.node .picture {
  border: 1px solid #ddd;
  float: right; /* LTR */
  margin: 0.5em;
}
.comment {
  border: 1px solid #abc;
  padding: .5em;
  margin-bottom: 1em;
}
.comment .title a {
  font-size: 1.1em;
  font-weight: normal;
}
.comment .new {
  text-align: right; /* LTR */
  font-weight: bold;
  font-size: 0.8em;
  float: right; /* LTR */
  color: red;
}
.comment .picture {
  border: 1px solid #abc;
  float: right; /* LTR */
  margin: 0.5em;
}

/*
** Module specific styles
*/
#aggregator .feed-source {
  background-color: #eee;
  border: 1px solid #ccc;
  padding: 1em;
  margin: 1em 0;
}
#aggregator .news-item .categories, #aggregator .source, #aggregator .age {
  color: #999;
  font-style: italic;
  font-size: 0.9em;
}
#aggregator .title {
  margin-bottom: 0.5em;
  font-size: 1em;
}
#aggregator h3 {
  margin-top: 1em;
}
#forum table {
  width: 100%;
}
#forum td {
  padding: 0.5em;
}
#forum td.forum, #forum td.posts {
  background-color: #eee;
}
#forum td.topics, #forum td.last-reply {
  background-color: #ddd;
}
#forum td.container {
  background-color: #ccc;
}
#forum td.container a {
  color: #555;
}
#forum td.statistics, #forum td.settings, #forum td.pager {
  height: 1.5em;
  border: 1px solid #bbb;
}
#forum td .name {
  color: #96c;
}
#forum td .links {
  padding-top: 0.7em;
  font-size: 0.9em;
}
#profile .profile {
  clear: both;
  border: 1px solid #abc;
  padding: .5em;
  margin: 1em 0em;
}
#profile .profile .name {
  padding-bottom: 0.5em;
}
.block-forum h3 {
  margin-bottom: .5em;
}
div.admin-panel .description {
  color: #999;
}
div.admin-panel .body {
  background: #f4f4f4;
}
div.admin-panel h3 {
  background-color: #69c;
  color: #fff;
  padding: 5px 8px 5px;
  margin: 0;
}
/* $Id: style.css,v 1.23 2007/12/17 15:05:09 goba Exp $ */

/*
** HTML elements
*/
body {
  margin-top:15px;
  margin-bottom:15px;
  padding: 0;
  background-color: #E1ECE1;
  margin-left:auto;
  margin-right:auto;
  font-size: 11px;
  font-family: Verdana, Arial, SunSans-Regular, Sans-Serif;
  color:#003300;
  /* margin:0; */
}
tr.odd td, tr.even td {
  padding: 0.3em;
}

h1, h2, h3, h4, h5, h6 {
  margin-bottom: 0.5em;
}
h1 {
  font-size: 1.3em;
}
h2 {
  font-size: 1.2em;
}
h3, h4, h5, h6 {
  font-size: 1.1em;
}
h7 {
font-size: 10px;
text-transform:uppercase;
text-align:right;
background-color:#669966;
border-top:1px solid #564b47;
border-bottom:1px solid #564b47;
padding:2px 6px;
margin:0;
width: 100%; 
}

p {
  margin-top: 0.5em;
  margin-bottom: 0.9em;
}
a {
  text-decoration: none;
  /* font-weight: bold; */
}
a:link {
  color: #000099;
}
a:visited {
  color: #336699;
}
a:hover {
  color: #00004D;
  text-decoration: underline;
}
fieldset {
  border: 1px solid #ccc;
}
pre {
  background-color: #eee;
  padding: 0.75em 1.5em;
  font-size: 12px;
  border: 1px solid #ddd;
}
table {
  /* make <td> sizes relative to body size! */
  font-size: 1em;
  margin-left:auto;
  margin-right:auto;
}
.form-item label {
  font-size: 1em;
  color: #002400;
}
.item-list .title {
  font-size: 1em;
  color: #002400;
}
.links {
  margin-bottom: 0;
}
.comment .links {
  margin-bottom: 0;
}

/*
** Page layout blocks / IDs
*/
#header, #content {
  width: 95%;
}
#header {
  background-color: #a8c79d;
  margin-left:auto;
  margin-right:auto;
  padding:0px 0px; 
}

#logo {
  vertical-align: middle;
  width:100%;
  margin-right:0px;
  padding:0px 0px; 
  border: 0;
}
#logo img {
  float: right; /* LTR */
  border: 0;
  padding:0px 0px; 
}
#menu {
  padding: 0.0em 0.0em 0 0.0em; /* LTR */
  text-align: right; /* LTR */
  vertical-align: middle;
}
#navlist {
  font-size: 1.0em;
  padding: 0 0.8em 1.2em 0; /* LTR */
  color: #9cf;
}
#navlist a {
  font-weight: bold;
  color: #fff;
}
#subnavlist {
  padding: 0.5em 1.2em 0.4em 0; /* LTR */
  font-size: 0.8em;
  color: #9cf;
}
#subnavlist a {
  font-weight: bold;
  color: #9cf;
}
ul.links li {
  border-left: 1px solid #9cf; /* LTR */
}
ul.links li.first {
  border: none;
}
#search .form-text, #search .form-submit {
  border: 1px solid #369;
  font-size: 1.1em;
  height: 1.5em;
  vertical-align: middle;
}
#search .form-text {
  width: 8em;
  padding: 0 0.5em;
}
#mission {
  background-color: #369;
  padding: 1.5em 2em;
  color: #fff;
}
#mission a, #mission a:visited {
  color: #9cf;
  font-weight: bold;
}
.site-name {
  margin: 0.6em 0 0 ;
  padding: 0;
  font-size: 2em;
}
.site-name a:link, .site-name a:visited {
  color: #fff;
}
.site-name a:hover {
  color: #369;
  text-decoration: none;
}
.site-slogan {
  font-size: 1em;
  color: #eee;
  display: block;
  margin: 0;
  font-style: italic;
  font-weight: bold;
}
#main {
  /* padding in px not ex because IE messes up 100% width tables otherwise */
  padding: 10px;
}
#mission, .node .content, .comment .content {
  line-height: 1.4em;
}
#help {
  font-size: 0.9em;
  margin-bottom: 1em;
}
.breadcrumb {
  margin-bottom: .5em;
}
.messages {
  background-color: #eee;
  border: 1px solid #ccc;
  padding: 0.3em;
  margin-bottom: 1em;
}
.error {
  border-color: red;
}
#sidebar-left{
  background-color: #7ab469;
  width: 16em;
  /* padding in px not ex because IE messes up 100% width tables otherwise */
  padding: 10px;
  vertical-align: top;
}

#sidebar-right {
  background-color: #bfd788;
  width: 16em;
  /* padding in px not ex because IE messes up 100% width tables otherwise */
  padding: 10px;
  vertical-align: top;

bfd788;
}

#footer {
  background-color: #669966;
  padding: 5px -2px;
  margin-left:auto;
  margin-right:auto;
  font-size: 0.8em;
  width: 95%;
}

/*
** Common declarations for child classes of node, comment, block, box, etc.
** If you want any of them styled differently for a specific parent, add
** additional rules /with only the differing properties!/ to .parent .class.
** See .comment .title for an example.
*/
.title, .title a {
  font-weight: bold;
  font-size: 1.3em;
  color: #002400;
  margin: 0 auto;  /* decrease default margins for h<x>.title */
}
.submitted {
  color: #999;
  font-size: 0.8em;
}
.links {
  color: #999;
}
.links a {
  font-weight: bold;
}
.block, .box {
  padding: 0 0 1.5em 0; /* LTR */
}
.block {
  border-bottom: 1px solid #bbb;
  padding-bottom: 0.75em;
  margin-bottom: 1.5em;
}
.block .title {
  margin-bottom: .25em;
}
.box .title {
  font-size: 1.1em;
}
.node {
  margin: .5em 0 2em; /* LTR */
}
.sticky {
  padding: .5em;
  background-color: #eee;
  border: solid 1px #ddd;
}
.node .content, .comment .content {
  margin: .5em 0 .5em;
}
.node .taxonomy {
  color: #999;
  font-size: 0.8em;
  padding-left: 1.5em; /* LTR */
}
.node .picture {
  border: 1px solid #ddd;
  float: right; /* LTR */
  margin: 0.5em;
}
.comment {
  border: 1px solid #abc;
  padding: .5em;
  margin-bottom: 1em;
}
.comment .title a {
  font-size: 1.1em;
  font-weight: normal;
}
.comment .new {
  text-align: right; /* LTR */
  font-weight: bold;
  font-size: 0.8em;
  float: right; /* LTR */
  color: red;
}
.comment .picture {
  border: 1px solid #abc;
  float: right; /* LTR */
  margin: 0.5em;
}

/*
** Module specific styles
*/
#aggregator .feed-source {
  background-color: #eee;
  border: 1px solid #ccc;
  padding: 1em;
  margin: 1em 0;
}
#aggregator .news-item .categories, #aggregator .source, #aggregator .age {
  color: #999;
  font-style: italic;
  font-size: 0.9em;
}
#aggregator .title {
  margin-bottom: 0.5em;
  font-size: 1em;
}
#aggregator h3 {
  margin-top: 1em;
}
#forum table {
  width: 100%;
}
#forum td {
  padding: 0.5em;
}
#forum td.forum, #forum td.posts {
  background-color: #eee;
}
#forum td.topics, #forum td.last-reply {
  background-color: #ddd;
}
#forum td.container {
  background-color: #ccc;
}
#forum td.container a {
  color: #555;
}
#forum td.statistics, #forum td.settings, #forum td.pager {
  height: 1.5em;
  border: 1px solid #bbb;
}
#forum td .name {
  color: #96c;
}
#forum td .links {
  padding-top: 0.7em;
  font-size: 0.9em;
}
#profile .profile {
  clear: both;
  border: 1px solid #abc;
  padding: .5em;
  margin: 1em 0em;
}
#profile .profile .name {
  padding-bottom: 0.5em;
}
.block-forum h3 {
  margin-bottom: .5em;
}
div.admin-panel .description {
  color: #999;
}
div.admin-panel .body {
  background: #f4f4f4;
}
div.admin-panel h3 {
  background-color: #69c;
  color: #fff;
  padding: 5px 8px 5px;
  margin: 0;
}
/* $Id: style.css,v 1.23 2007/12/17 15:05:09 goba Exp $ */

/*
** HTML elements
*/
body {
  margin-top:15px;
  margin-bottom:15px;
  padding: 0;
  background-color: #E1ECE1;
  margin-left:auto;
  margin-right:auto;
  font-size: 11px;
  font-family: Verdana, Arial, SunSans-Regular, Sans-Serif;
  color:#003300;
  /* margin:0; */
}
tr.odd td, tr.even td {
  padding: 0.3em;
}

h1, h2, h3, h4, h5, h6 {
  margin-bottom: 0.5em;
}
h1 {
  font-size: 1.3em;
}
h2 {
  font-size: 1.2em;
}
h3, h4, h5, h6 {
  font-size: 1.1em;
}
/* h7 {
font-size: 10px;
text-transform:uppercase;
background-color:#669966;
border-top:1px solid #564b47;
border-bottom:1px solid #564b47;
padding:2px 6px;
margin:0 } */
p {
  margin-top: 0.5em;
  margin-bottom: 0.9em;
}
a {
  text-decoration: none;
  /* font-weight: bold; */
}
a:link {
  color: #000099;
}
a:visited {
  color: #336699;
}
a:hover {
  color: #00004D;
  text-decoration: underline;
}
fieldset {
  border: 1px solid #ccc;
}
pre {
  background-color: #eee;
  padding: 0.75em 1.5em;
  font-size: 12px;
  border: 1px solid #ddd;
}
table {
  /* make <td> sizes relative to body size! */
  font-size: 1em;
  margin-left:auto;
  margin-right:auto;
}
.form-item label {
  font-size: 1em;
  color: #002400;
}
.item-list .title {
  font-size: 1em;
  color: #002400;
}
.links {
  margin-bottom: 0;
}
.comment .links {
  margin-bottom: 0;
}

/*
** Page layout blocks / IDs
*/
#header, #content {
  width: 95%;
}
#header {
  background-color: #a8c79d;
  margin-left:auto;
  margin-right:auto;
  padding:0px 0px; 
}

#logo {
  vertical-align: middle;
  width:100%;
  margin-right:0px;
  padding:0px 0px; 
  border: 0;
}
#logo img {
  float: right; /* LTR */
  border: 0;
  padding:0px 0px; 
}
#menu {
  padding: 0.0em 0.0em 0 0.0em; /* LTR */
  text-align: right; /* LTR */
  vertical-align: middle;
}
#navlist {
  font-size: 1.0em;
  padding: 0 0.8em 1.2em 0; /* LTR */
  color: #9cf;
}
#navlist a {
  font-weight: bold;
  color: #fff;
}
#subnavlist {
  padding: 0.5em 1.2em 0.4em 0; /* LTR */
  font-size: 0.8em;
  color: #9cf;
}
#subnavlist a {
  font-weight: bold;
  color: #9cf;
}
ul.links li {
  border-left: 1px solid #9cf; /* LTR */
}
ul.links li.first {
  border: none;
}
#search .form-text, #search .form-submit {
  border: 1px solid #369;
  font-size: 1.1em;
  height: 1.5em;
  vertical-align: middle;
}
#search .form-text {
  width: 8em;
  padding: 0 0.5em;
}
#mission {
  background-color: #369;
  padding: 1.5em 2em;
  color: #fff;
}
#mission a, #mission a:visited {
  color: #9cf;
  font-weight: bold;
}
.site-name {
  margin: 0.6em 0 0 ;
  padding: 0;
  font-size: 2em;
}
.site-name a:link, .site-name a:visited {
  color: #fff;
}
.site-name a:hover {
  color: #369;
  text-decoration: none;
}
.site-slogan {
  font-size: 1em;
  color: #eee;
  display: block;
  margin: 0;
  font-style: italic;
  font-weight: bold;
}
#main {
  /* padding in px not ex because IE messes up 100% width tables otherwise */
  padding: 10px;
}
#mission, .node .content, .comment .content {
  line-height: 1.4em;
}
#help {
  font-size: 0.9em;
  margin-bottom: 1em;
}
.breadcrumb {
  margin-bottom: .5em;
}
.messages {
  background-color: #eee;
  border: 1px solid #ccc;
  padding: 0.3em;
  margin-bottom: 1em;
}
.error {
  border-color: red;
}
#sidebar-left{
  background-color: #7ab469;
  width: 16em;
  /* padding in px not ex because IE messes up 100% width tables otherwise */
  padding: 10px;
  vertical-align: top;
}

#sidebar-right {
  background-color: #bfd788;
  width: 16em;
  /* padding in px not ex because IE messes up 100% width tables otherwise */
  padding: 10px;
  vertical-align: top;

bfd788;
}

#footer {
  background-color: #669966;
  padding: 5px -2px;
  margin-left:auto;
  margin-right:auto;
  font-size: 0.8em;
  width: 95%;
}

/*
** Common declarations for child classes of node, comment, block, box, etc.
** If you want any of them styled differently for a specific parent, add
** additional rules /with only the differing properties!/ to .parent .class.
** See .comment .title for an example.
*/
.title, .title a {
  font-weight: bold;
  font-size: 1.3em;
  color: #002400;
  margin: 0 auto;  /* decrease default margins for h<x>.title */
}
.submitted {
  color: #999;
  font-size: 0.8em;
}
.links {
  color: #999;
}
.links a {
  font-weight: bold;
}
.block, .box {
  padding: 0 0 1.5em 0; /* LTR */
}
.block {
  border-bottom: 1px solid #bbb;
  padding-bottom: 0.75em;
  margin-bottom: 1.5em;
}
.block .title {
  margin-bottom: .25em;
}
.box .title {
  font-size: 1.1em;
}
.node {
  margin: .5em 0 2em; /* LTR */
}
.sticky {
  padding: .5em;
  background-color: #eee;
  border: solid 1px #ddd;
}
.node .content, .comment .content {
  margin: .5em 0 .5em;
}
.node .taxonomy {
  color: #999;
  font-size: 0.8em;
  padding-left: 1.5em; /* LTR */
}
.node .picture {
  border: 1px solid #ddd;
  float: right; /* LTR */
  margin: 0.5em;
}
.comment {
  border: 1px solid #abc;
  padding: .5em;
  margin-bottom: 1em;
}
.comment .title a {
  font-size: 1.1em;
  font-weight: normal;
}
.comment .new {
  text-align: right; /* LTR */
  font-weight: bold;
  font-size: 0.8em;
  float: right; /* LTR */
  color: red;
}
.comment .picture {
  border: 1px solid #abc;
  float: right; /* LTR */
  margin: 0.5em;
}

/*
** Module specific styles
*/
#aggregator .feed-source {
  background-color: #eee;
  border: 1px solid #ccc;
  padding: 1em;
  margin: 1em 0;
}
#aggregator .news-item .categories, #aggregator .source, #aggregator .age {
  color: #999;
  font-style: italic;
  font-size: 0.9em;
}
#aggregator .title {
  margin-bottom: 0.5em;
  font-size: 1em;
}
#aggregator h3 {
  margin-top: 1em;
}
#forum table {
  width: 100%;
}
#forum td {
  padding: 0.5em;
}
#forum td.forum, #forum td.posts {
  background-color: #eee;
}
#forum td.topics, #forum td.last-reply {
  background-color: #ddd;
}
#forum td.container {
  background-color: #ccc;
}
#forum td.container a {
  color: #555;
}
#forum td.statistics, #forum td.settings, #forum td.pager {
  height: 1.5em;
  border: 1px solid #bbb;
}
#forum td .name {
  color: #96c;
}
#forum td .links {
  padding-top: 0.7em;
  font-size: 0.9em;
}
#profile .profile {
  clear: both;
  border: 1px solid #abc;
  padding: .5em;
  margin: 1em 0em;
}
#profile .profile .name {
  padding-bottom: 0.5em;
}
.block-forum h3 {
  margin-bottom: .5em;
}
div.admin-panel .description {
  color: #999;
}
div.admin-panel .body {
  background: #f4f4f4;
}
div.admin-panel h3 {
  background-color: #69c;
  color: #fff;
  padding: 5px 8px 5px;
  margin: 0;
}

```

php
```

<?php
// $Id: page.tpl.php,v 1.28.2.1 2009/04/30 00:13:31 goba Exp $
?><!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" lang="<?php print $language->language ?>" xml:lang="<?php print $language->language ?>" dir="<?php print $language->dir ?>">

<head>
  <?php print $head ?>
  <title><?php print $head_title ?></title>
  <?php print $styles ?>
  <?php print $scripts ?>
  <script type="text/javascript"><?php /* Needed to avoid Flash of Unstyle Content in IE */ ?> </script>
</head>

<body>

<table border="0" cellpadding="0" cellspacing="0" id="header">
  <tr>
    <td id="logo">
      <?php if ($logo) { ?><a href="<?php print $front_page ?>" title="<?php print t('Home') ?>"><img src="<?php print $logo ?>" alt="<?php print t('Home') ?>" /></a><?php } ?>
      <?php if ($site_name) { ?><h1 class='site-name'><a href="<?php print $front_page ?>" title="<?php print t('Home') ?>"><?php print $site_name ?></a></h1><?php } ?>
      <?php if ($site_slogan) { ?><div class='site-slogan'><?php print $site_slogan ?></div><?php } ?>
    </td>
    <td id="menu">
      <?php if (isset($secondary_links)) { ?><?php print theme('links', $secondary_links, array('class' => 'links', 'id' => 'subnavlist')) ?><?php } ?>
      <?php if (isset($primary_links)) { ?><?php print theme('links', $primary_links, array('class' => 'links', 'id' => 'navlist')) ?><?php } ?>
      <?php print $search_box ?>
    </td>
  </tr>
  
  <tr>
      <td width="600" align="right">
		<h7>woohoo</h7>
    </td>
  </tr>
  
  <tr>
    <td colspan="2"><div><?php print $header ?></div></td>
  </tr>
</table>

<table border="0" cellpadding="0" cellspacing="0" id="content">
  <tr>
    <?php if ($left) { ?><td id="sidebar-left">
      <?php print $left ?>
    </td><?php } ?>
    <td valign="top">
      <?php if ($mission) { ?><div id="mission"><?php print $mission ?></div><?php } ?>
      <div id="main">
        <?php print $breadcrumb ?>
        <h1 class="title"><?php print $title ?></h1>
        <div class="tabs"><?php print $tabs ?></div>
        <?php if ($show_messages) { print $messages; } ?>
        <?php print $help ?>
        <?php print $content; ?>
        <?php print $feed_icons; ?>
      </div>
    </td>
    <?php if ($right) { ?><td id="sidebar-right">
      <?php print $right ?>
    </td><?php } ?>
  </tr>
</table>

<div id="footer">
  <?php print $footer_message ?>
  <?php print $footer ?>
</div>
<?php print $closure ?>
</body>
</html>

```

---

### Post by Rebajas on 2010-06-14
Try an element other than h7 - h7 doesn't exist, goes h1-h6.

Not sure if that will help though...

---

### Post by DanielWaterworth on 2010-06-15
Using Firebug, changing the element to a h6 works.

---

### Post by cdaringe on 2010-06-16
you guys are great!
thanks.
Firebug, huh?  maybe ill give that a whirl...

---

### Post by mainerror on 2010-06-16
> **cdaringe said:**
> you guys are great!
thanks.
Firebug, huh?  maybe ill give that a whirl...

You gotta try Firebug. It will ease your life believe me. ;)

---

### Post by DanielWaterworth on 2010-06-16
I wouldn't be able to pretend I can do web development without FireBug =D. (I can really, see, look, website, vvvv)

---

