---
title: "[wxPython] Deleting Class Instance to Free Memory"
date: 2011-08-18
forum: Programming Talk
---

### Post by dodle on 2011-08-18
I have created a parent class with a method that will delete one of its child classes. But I don't know if this is the right way to free up all the memory. The method is located in the [color=red]RemoveTile[/color] method of the [color=red]Canvas[/color] class:

[php]import wxversion

wxversion.select(['2.6', '2.7', '2.8'])

import wx

class Tile():
    def __init__(self, parent, id, image):
        
        self.id = id
        
        self.image = wx.Image(image)
        self.bg = wx.StaticBitmap(parent, -1, self.image.ConvertToBitmap())
    
    def GetId(self):
        return self.id


class Canvas(wx.Panel):
    def __init__(self, parent, id=wx.NewId()):
        wx.Panel.__init__(self, parent, id)
        
        self.tile_list = []
    
    def AddTile(self, id, image):
        self.tile_list.append(Tile(self, id, image))
    
    def RemoveTile(self, id):
        """ This method should remove the child instance and all of its members to free up memory """
        for tile in self.tile_list:
            if tile.GetId() == id:
                self.tile_list.remove(tile)
                del tile.id
                del tile.image
                tile.bg.Destroy()
                del tile[/php]

So, have I done a good job freeing up memory or have I totally missed something?

---

### Post by cgroza on 2011-08-18
You should only remove your tile from the list, and let the garbage collector take care of it.
When you do del tile, you only remove the name tile, the references to tiles still remain in the list and since the object are still referenced, the garbage collector won't free them.

---

### Post by dodle on 2011-08-18
If I only delete the tile from the list the tile stays on the screen.

---

### Post by cgroza on 2011-08-18
I just noticed that you already remove the tile from the tile_list. The garbage collector should take care of it.
No need for all the "del" since that only removes the reference and not the real objects.
No need to "del" the Tile members either, because when a there is no way to access anything in that Tile, the garbage collector will remove it.

So far you only need to call Destroy on your StaticBitmap and to remove the Tile from the list so it becomes unreferenced.

---

### Post by dodle on 2011-08-18
Okay, I guess I just don't understand garbage collection. I thought it occurred at program termination.

---

