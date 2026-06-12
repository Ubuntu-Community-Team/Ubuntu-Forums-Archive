---
title: "actionscript hitTest question"
date: 2008-09-14
forum: Programming Talk
---

### Post by Zigon on 2008-09-14
I'm trying to make multiple squares that the player can't pass through. The problem I'm having is that when I make one, the other won't work because it's using the same global variables I have set up. I was wondering if there was a way I could do this without having to have each square have it's own variable; if they could all use the same global vars. 

Frame:
```
_root.axe = _root.player._y + " , " + _root.player._x;
_global.mdown = true;
_global.mup = true;
_global.mleft = true;
_global.mright = true;
_global.touching = false;
stop();
```

Character:
```
onClipEvent (enterFrame) {
	if (Key.isDown(Key.DOWN)) {
		if (_global.mdown == true) {
		_root.axe = _root.player._y + " , " + _root.player._x;
		this._y += 5;
	}
	}
	if (Key.isDown(Key.UP)) {
		if (_global.mup == true) {
		_root.axe = _root.player._y + " , " + _root.player._x;
		this._y -= 5;
		}
	}
	if (Key.isDown(Key.LEFT)) {
		if (_global.mleft == true) {
		_root.axe = _root.player._y + " , " + _root.player._x;
		this._x -= 5;
		}
	}
	if (Key.isDown(Key.RIGHT)) {
		if (_global.mright == true) {
		_root.axe = _root.player._y + " , " + _root.player._x;
		this._x += 5;
	}
	}
	if (this._x>50 or this._x<=0) {
		this.y += 5;
	}
	if(touching == true){
		
	}
}

```

Side of square:
```
onClipEvent(enterFrame){
	if(this.hitTest(_root.player)){
		_global.mdown = false;
		
	}else{
		_global.mdown = true;
	}
}
```

For the square all I did was take 4 lines and put them together. This is the code for the top of the square, the left side of the square would be ```
_global.mright = false;
```

---

