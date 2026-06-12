---
title: "Is it a bug in flash player 9?"
date: 2009-02-08
forum: Programming Talk
---

### Post by cl333r on 2009-02-08
Hi folks,
According to the small test below the flash player 9 (on Ubuntu) seems to have a buggy coordinate system. As you can see on the screenshots version 10 works fine - the cross comes right in the middle.
Does anyone know a workaround to this bug from player v9?
It's important to me cause like 40% still have version 9 and I wanna make sure my code works fine on it.

Test:
```

package {
	import flash.display.Sprite;
	
	public class Main extends Sprite {
		
		public function Main() {
			init();
			graphics.lineStyle(1);
			var w:int = stage.stageWidth;
			var h:int = stage.stageHeight;
			
			graphics.moveTo(0,h/2);
			graphics.lineTo(w,h/2);
			
			graphics.moveTo(w/2,0);
			graphics.lineTo(w/2,h);
			
		}
		
		private function init():void {
			w.x = stage.stageWidth/2 - w.getLength();
			w.y = stage.stageHeight/2 + 20;
		}
	}
}

```

---

