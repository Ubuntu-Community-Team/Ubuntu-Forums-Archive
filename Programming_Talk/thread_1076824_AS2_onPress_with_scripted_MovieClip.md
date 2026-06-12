---
title: "AS2 onPress with scripted MovieClip"
date: 2009-02-21
forum: Programming Talk
---

### Post by Rahzizzle on 2009-02-21
So I am building a PhotoGallery that reads in data from an XML file, jpegURL and thumbURL are the locations of the pictures.

This is my code
function loadSlideShow(success) {
	if (success == true) {
		rootNode = slides_xml.firstChild; 
		totalSlides = rootNode.childNodes.length;
		currentSlideNode = rootNode.firstChild;                             
		photos = new Array(totalSlides);
		thumbs = new Array(totalSlides);
		captions = new Array(totalSlides);			
		thumbnails = new Array(totalSlides);
		var currentThumb;
		tx = 0;
		for (i=0; i < totalSlides; i++) { // populate arrays and create thumbnails dynamically
			photos[i] = currentSlideNode.attributes.jpegURL; 
			thumbs[i] = [currentSlideNode.attributes.jpegWidth,currentSlideNode.attributes.jpegHeight];
			thumbnails[i] = currentSlideNode.attributes.thumbURL;
			captions[i] = currentSlideNode.firstChild.nodeValue;
			this.createEmptyMovieClip("thumb"+i, i);
			'Thumbs'
			'currentThumb = _root.attachMovie("thumbHolder", "thumb" + i, i);'
			
			
			_root.attachMovie("thumb" , "thumb"+i, i);
			
			_root["thumb"+i]._x = tx;
			_root["thumb"+i]._y = 300; // using fixed Y coord
			_root["thumb"+i].width = 85;
			_root["thumb"+i].height = 85;
			_root["thumb"+i].tindex = i;
			_root["thumb"+i].border = 2;
			
			loadMovie(thumbnails[i], "thumb"+i);

			[B]_root["thumb"+i].onPress = function() {
				currentIndex = i;
                                updateSlide();
			}[/B]
                        [B]_root["thumb"+i].onRollOver = function() {
				_root["thumb"+i]._alpha = 40;
			}[/B]
			tx += 90;			
			currentSlideNode = currentSlideNode.nextSibling;
		}
		// initialize values
			
		currentIndex = 0;
		targetWidth=thumbs[currentIndex][0]; // get width
		targetHeight=thumbs[currentIndex][1]; // get height;
		updateSlide();
	}
}

It works perfect but the only thing that doesn't work is the onPress and onRollOver events for the thumbnails. I have tried moving that statement elsewhere but I am just exhausted from today and don't want to even try anything more. If someone can spot an error right away I'd be very appreciative, thanks

-Aaron DaMaster :confused:

---

### Post by Can+~ on 2009-02-21
> **Rahzizzle said:**
> So I am building a PhotoGallery that reads in data from an XML file, jpegURL and thumbURL are the locations of the pictures.

This is my code
[PHP]function loadSlideShow(success) {
	if (success == true) {
		rootNode = slides_xml.firstChild; 
		totalSlides = rootNode.childNodes.length;
		currentSlideNode = rootNode.firstChild;                             
		photos = new Array(totalSlides);
		thumbs = new Array(totalSlides);
		captions = new Array(totalSlides);			
		thumbnails = new Array(totalSlides);
		var currentThumb;
		tx = 0;
		for (i=0; i < totalSlides; i++) { // populate arrays and create thumbnails dynamically
			photos[i] = currentSlideNode.attributes.jpegURL; 
			thumbs[i] = [currentSlideNode.attributes.jpegWidth,currentSlideNode.attributes.jpegHeight];
			thumbnails[i] = currentSlideNode.attributes.thumbURL;
			captions[i] = currentSlideNode.firstChild.nodeValue;
			this.createEmptyMovieClip("thumb"+i, i);
			'Thumbs'
			'currentThumb = _root.attachMovie("thumbHolder", "thumb" + i, i);'
			
			
			_root.attachMovie("thumb" , "thumb"+i, i);
			
			_root["thumb"+i]._x = tx;
			_root["thumb"+i]._y = 300; // using fixed Y coord
			_root["thumb"+i].width = 85;
			_root["thumb"+i].height = 85;
			_root["thumb"+i].tindex = i;
			_root["thumb"+i].border = 2;
			
			loadMovie(thumbnails[i], "thumb"+i);

			_root["thumb"+i].onPress = function() {
				currentIndex = i;
                                updateSlide();
			}
                        _root["thumb"+i].onRollOver = function() {
				_root["thumb"+i]._alpha = 40;
			}
			tx += 90;			
			currentSlideNode = currentSlideNode.nextSibling;
		}
		// initialize values
			
		currentIndex = 0;
		targetWidth=thumbs[currentIndex][0]; // get width
		targetHeight=thumbs[currentIndex][1]; // get height;
		updateSlide();
	}
}[/PHP]

It works perfect but the only thing that doesn't work is the onPress and onRollOver events for the thumbnails. I have tried moving that statement elsewhere but I am just exhausted from today and don't want to even try anything more. If someone can spot an error right away I'd be very appreciative, thanks

-Aaron DaMaster :confused:

If I remember correctly, when using the movieclip.event = function syntax in AS2, the following block is considered all "inside" said MovieClip. When buttons, on the contrary, recognize the block as part of the place where they are.

First of all, try putting a [FONT="Courier New"]trace("Im being clicked/rollovered");[/FONT] inside those two functions and see if the functions is actually being called.

If it's called, then try setting: 

[PHP]_root["thumb"+i].onRollOver = function() {
    this._alpha = 40;
}[/PHP]

And I guess that updateSlide() is on the _root, so it should probably be:

[PHP]_root["thumb"+i].onPress = function() {
    _root.currentIndex = i;
    _root.updateSlide();
}[/PHP]

Long time I don't use AS2.

---

### Post by Rahzizzle on 2009-02-24
Thanks for the input. I actually solved the problem by scrapping AS2 and completely re-writing it for AS3 and it works like a charm!

Done, Done, and I'm on to the next one...

---

