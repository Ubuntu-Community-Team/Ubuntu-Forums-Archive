---
title: "Problem Window Resize with FF 3.0"
date: 2008-09-10
forum: Programming Talk
---

### Post by charlievos on 2008-09-10
Hi,

I'm using the following script to resize a new window. But it doesn't work in FF3.0 on UBUNTU. Can someone please give me a clue?

grtz,
CV

// Code to force a minimum siez of a window
var minW = 800; // wanted widht of the screen
var minH = 700; // wanted height of the screen
 
function getPageWH(xPart) {
	if( typeof window.innerWidth  == 'number' ) {
    	pageW = window.innerWidth;
    	pageH = window.innerHeight;
	} 
	else if(document.documentElement && 
             document.documentElement.clientWidth ) {
    	pageW = document.documentElement.clientWidth;
    	pageH = document.documentElement.clientHeight;
	} 
	else {
    	pageW = document.body.clientWidth;
    	pageH = document.body.clientHeight;
	}
	if(xPart=="w")return pageW;
	else return pageH
}

function VerifySize() {
	var resizeMe = false;
	var winW = parseInt(getPageWH("w"));
	var winH = parseInt(getPageWH("h"));
	if(minW>winW) {
		winW=minW;
		resizeMe=true;
	}
	if(minH>winH) {
		winH=minH;
		resizeMe=true;
	}

	if(resizeMe) {
		window.resizeTo(winW,winH);
		var winW2 = winW - parseInt(getPageWH("w"));
		var winH2 = winH - parseInt(getPageWH("h"));
		window.resizeTo(winW + winW2,winH + winH2);
	}
	document.getElementById("tooltip").innerHTML = "(" + parseInt(getPageWH("w")) + "," + parseInt(getPageWH("h")) + ")";
}

---

