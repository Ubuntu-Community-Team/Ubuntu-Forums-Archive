---
title: "java mime type for linux"
date: 2008-04-15
forum: Programming Talk
---

### Post by christoforever on 2008-04-15
Im programming a java app with drag and drop. When the user drags a picture over a specific panel, the panel grabs the picture and thats the users new pic. The problem is that when I do this the panel instead of grabbing the pic and repainting the panel it just turns gray. I did a bit of debugging and it does grab the pic but it doesent paint it properly back on. Now heres the kicker...I brought the program to a friends house to run it on his windows machine and it worked flawlesssly. This really upset me. Anyway, does anyone have any ideas?


sincerely,
Chris Dancy

---

### Post by Zugzwang on 2008-04-15
Ok, so the panel turns gray. Did you check if the image was really loaded? Do you get any exceptions? Do you use an ImageObserver which gets the errors that occur while loading the image reported? Does it receive an error?

---

### Post by christoforever on 2008-04-17
I get no errors at all nothing. I've never used image observer before so im not sure as to its use. Either way everything loads fine, the image loads fine. Remember this does work under windows with the exact same picture that i use to drag and drop. Im really not sure what to do next?

---

### Post by Zugzwang on 2008-04-17
How do you check if the image loads fine if you don't use an ImageObserver? 

Have you tried paining the image to a BufferedImage and saving that to "/tmp/test.png" instead of drawing it onto the panel? The error could occur at either drawing or loading. 

Note that the image might not be loaded yet when you try to paint it on the Panel. In this case you could try to load it using [ImageIO.read]("http://java.sun.com/j2se/1.5.0/docs/api/javax/imageio/ImageIO.html#read(java.io.File)") which does not use asynchronous(?) loading.

---

### Post by ZylGadis on 2008-04-17
Java programs should work the same everywhere. If his program works fine on Windows, then it should do so on GNU/Linux too, unless there is a bug in the GNU/Linux implementation of the platform.

Coincidentally, there is a bug which results in just what the OP describes (awt panels turning gray), even though under slightly different conditions, so I'd say that is the cause. OP, check your java -version. Java 5 has the bug, as does Java 6 update 1 and 2. I think it has been fixed since Java 6 update 3.

---

### Post by Zugzwang on 2008-04-17
> **ZylGadis said:**
> Java programs should work the same everywhere. If his program works fine on Windows, then it should do so on GNU/Linux too, unless there is a bug in the GNU/Linux implementation of the platform.


Well, they should, but they don't and this is mostly due to mistakes when designing the software. For example, many people forget to use "File.separatorChar" instead of "\" or "/" which prevents portability when loading/saving files if the filename is manipulated. 

What the OP describes might have the following cause: Image loading is typically performed asynchronously in Java and this might cause a so called race condition. It is well possible that these do not occur on Windows but on Linux due to different schedulers and/or Java implementations. Since Java won't raise an exception when trying to paint the not-yet-loaded image, this might be the cause which is to be checked.

But the bug you mentioned might of course also be the cause. :) OP, since updating Java takes less time, you might want to try this first.

---

### Post by christoforever on 2008-04-17
Here is the update. I am using ImageIO.read for bringing in the image through my drag and drop the image comes in as an imageicon and then i convert to image and then bufferedimage. when i save the image it shows nothing but a file name. here is the soure code. that problem ive tracked down comes at the very bottom in the waitforimage() method at the end of this there is a while loop the just runs forver never returning true. I commented out the bufferedimage code that you may see cause i was trying something new..


package profileCreatorGui;
import javax.swing.*;
import programStart.ImageLoader;
import java.awt.*;
import java.awt.datatransfer.DataFlavor;
import java.awt.datatransfer.Transferable;
import java.awt.dnd.*;
import java.awt.image.*;
import java.io.File;
import java.net.URL;
import java.util.Iterator;
import java.util.ListIterator;
import java.util.StringTokenizer;
import java.io.*;
import javax.imageio.*;
public class PicturePanel extends JPanel implements DropTargetListener{
	DropTarget dropTarget;
	static DataFlavor urlFlavor,uriListFlavor,uriListFlavor2,uriListFlavor3,macPictStreamFlavor;
	boolean imageHere = false;
	Image newDroppedImage;
	static {
		try{
			urlFlavor = new DataFlavor("application/x-java-url; class=java.net.URL");
			uriListFlavor = new DataFlavor("text/uri-list; class=java.lang.String");
			uriListFlavor2 = new DataFlavor("x-special/gnome-icon-list;representationclass=java.io.InputStream");
			//uriListFlavor3 = new DataFlavor("text/plain;representationclass=[B;charset=US-ASCII]");
		}catch(ClassNotFoundException e){
			e.printStackTrace();
		}
	}
	
	public PicturePanel(){
		dropTarget = new DropTarget(this,this);
		super.setSize(134,135);
		super.setPreferredSize(new Dimension(134,135));
		super.setMaximumSize(new Dimension(134,135));
		super.setMinimumSize(new Dimension(134,135));
		super.setDoubleBuffered(true);
		super.setBorder(BorderFactory.createRaisedBevelBorder());
		
	}
	public void dragEnter(DropTargetDragEvent dt){};
	public void dragExit(DropTargetEvent dt){};
	public void dragOver(DropTargetDragEvent dt){};
	public void dropActionChanged(DropTargetDragEvent dt){};
	
	private void dumpDataFlavors(Transferable trans){
		System.out.println("Flavors: ");
		DataFlavor[] flavors = trans.getTransferDataFlavors();
		for(int i = 0; i < flavors.length;i++){
			System.out.println("***" + i + ": " + flavors[i]);
		}
	}
	public void drop(DropTargetDropEvent dtde){
		System.out.println("drop");
		dtde.acceptDrop(DnDConstants.ACTION_COPY_OR_MOVE);
		Transferable trans = dtde.getTransferable();
		//dumpDataFlavors(trans);
		boolean gotData = false;
		try{
			if(trans.isDataFlavorSupported(DataFlavor.imageFlavor)){
				System.out.println("flavor supported");
				Image img = (Image)trans.getTransferData(DataFlavor.imageFlavor);
				newDroppedImage = bufferImage(img);
				gotData = true;
			}
			else if(trans.isDataFlavorSupported(DataFlavor.javaFileListFlavor)){
				System.out.println("javafilelist supported");
				java.util.List list =(java.util.List)trans.getTransferData(DataFlavor.javaFileListFlavor);
				ListIterator it = list.listIterator();
				while(it.hasNext()){
					File f = (File)it.next();
					ImageIcon img = new ImageIcon(f.getAbsolutePath());
					setNewImage(img);
				}
				gotData = true;
			}
			else if(trans.isDataFlavorSupported(uriListFlavor)){
				System.out.println("uri list supported");
				String uris = (String)trans.getTransferData(uriListFlavor);
				StringTokenizer izer = new StringTokenizer(uris, "\r\n");
				while(izer.hasMoreTokens()){
					String uri = izer.nextToken();
					//newDroppedImage = ImageIO.read(new URL(uri));
					ImageIcon icon = new ImageIcon(uri);
					setNewImage(icon);
				}
				gotData = true;
			}
			else if(trans.isDataFlavorSupported(urlFlavor)){
				System.out.println("url flavor is supported");
				URL url = (URL)trans.getTransferData(urlFlavor);
				Image img = ImageIO.read(url);
				setNewImage(img);
				gotData = true;
			}
		}catch(Exception e){
			e.printStackTrace();
		}finally{
			dtde.dropComplete(gotData);
		}
	}
	public void setNewImage(Image img){
		this.newDroppedImage = img;
		imageHere = true;
		super.repaint();
	}
	public void setNewImage(ImageIcon img){
		this.newDroppedImage = img.getImage();
		imageHere = true;
		super.repaint();
		System.out.println("got to setNewImage with icon");
	}
	
	
	public void paintComponent(Graphics g){
		super.paintComponent(g);
		if(!imageHere){
			g.drawImage(ImageLoader.getDefaultNoImage(),0,0,this.getWidth(),this.getHeight(),this);
			System.out.println("got here..");
		}else{
			System.out.println("beginning of repaint");
			//BufferedImage buff = bufferImage(newDroppedImage);
			System.out.println("got buff");
			Graphics g2d = g.create();
			g2d.drawImage(bufferImage(newDroppedImage),0,0,this.getWidth(),this.getHeight(),this);
			System.out.println("Seems ok");
			g2d.dispose();
			revalidate();
		}
	}
	
	
	
	public BufferedImage bufferImage(Image image) {
        BufferedImage bufferedImage = new BufferedImage(image.getWidth(null)+ 2, image.getHeight(null) + 2,BufferedImage.TYPE_INT_RGB);
        Graphics2D g = bufferedImage.createGraphics();
        g.drawImage(image, null, null);
        System.out.println("buff image got here");
        waitForImage(bufferedImage);
        System.out.println("buff image got a bit further");
 
        return bufferedImage;
    }

    private void waitForImage(BufferedImage bufferedImage) {
    	System.out.println("got to wait");
        final ImageLoadStatus imageLoadStatus = new ImageLoadStatus();
        bufferedImage.getHeight(new ImageObserver() {
            public boolean imageUpdate(Image img, int infoflags, int x, int y, int width, int height) {
                if (infoflags == ALLBITS) {
                	System.out.println("ok");
                    imageLoadStatus.heightDone = true;
                    return true;
                }
                System.out.println("not ok");
                return false;
            }
        });
        bufferedImage.getWidth(new ImageObserver() {
            public boolean imageUpdate(Image img, int infoflags, int x, int y, int width, int height) {
                if (infoflags == ALLBITS) {
                    imageLoadStatus.widthDone = true;
                    return true;
                }
                return false;
            }
        });
        
        while (!imageLoadStatus.widthDone && !imageLoadStatus.heightDone) {
        	System.out.println(" \n" + imageLoadStatus.widthDone + " " + imageLoadStatus.heightDone);
            try {
                Thread.sleep(300);
            } catch (Exception e) {
            	e.printStackTrace();
            }
        }
    }

    class ImageLoadStatus {

        public boolean widthDone = false;
        public boolean heightDone = false;
    }
}



Any help would be great

---

### Post by Zugzwang on 2008-04-18
Ok, so I haven't run your code since it's a little bit incomplete (It's just the panel, so I would have to create a frame for it myself)
[LIST]
[*] In method bufferImage, you use a graphics handle but don't dispose it properly afterwards
[*] You never have to wait for a BufferedImage - The name said that when the object exists, the picture is there. The image observer is only called if something changes, so you're of course waiting forever. Also you have to wait for the image you get via "Image img = (Image)trans.getTransferData(DataFlavor.imageFlavor);" and not for the BufferedImage.
[*] When you load a picture via bufferImage(...), you don't repaint the panel!
[*] Why do you load images differently depending on the type of the drag-and-drop message? It should be all the same. In one case you're using ImageIcon, in the other ImageIO.read(). For converting between URL, URI and file names (whenever possible) use the respective classes.
[/LIST]

I suggest that you look into MediaTrackers in the Java Tutorial as mentioned on the class documentation of ImageIcon.

Finally: Please use PHP-tags for pasting code here. :-) Good luck with your program!

---

