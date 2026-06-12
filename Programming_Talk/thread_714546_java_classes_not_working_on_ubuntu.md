---
title: "java classes not working on ubuntu"
date: 2008-03-03
forum: Programming Talk
---

### Post by brdohman on 2008-03-03
I am in the process of developing some java code for some custom applications that can run on linux. However, I am wanting to run my application at full screen. In windows I can use the code below, to get my jframe or applet to take up the entire screen, even over the task bars.

public static void main(String[] args) {

// initialize the Graphic device to default one
final GraphicsDevice myDevice = GraphicsEnvironment.getLocalGraphicsEnvironment(). getDefaultScreenDevice();

// create the frame
final JFrame test = new JFrame("Login Screen");

// set recomended attributes
test.setResizable(false);
test.setUndecorated(true);
// test.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE ); // we don't really need this because no mouse close is provided
test.addKeyListener(new KeyAdapter() {

@Override
public void keyReleased(KeyEvent e) {

super.keyReleased(e);
// code to kill off other events such as ALT-F4 on windows should go here
// lets provide a way out for now
if (e.getKeyCode() == KeyEvent.VK_ESCAPE) {
myDevice.setFullScreenWindow(null);
test.dispose();
System.exit(0);

}


}
});
System.out.println("before full screen");

// query for supported
if (myDevice.isFullScreenSupported()) {
System.out.println("full screen supported");
try {
myDevice.setFullScreenWindow(test);
} catch (Exception e) {
// if something goes wrong kill the window get back to desktop
myDevice.setFullScreenWindow(null);

e.printStackTrace();


}


}
}



If anyone is unaware on how to get this to work, does anyone know the code or a possible way to disable the mouse completely, only allowing the user to have keyboard input? Is it possible to turn the mouse on and off in the terminal?

Thanks

---

### Post by Zugzwang on 2008-03-04
To get rid of the task bar, you might want to run X in a "plain" mode, that means using a Window manager that doesn't have a task bar. For disabling the mouse, you can alter your Xorg.conf not to have mouse support.

I'm afraid that there is no pure Java support for doing so since I don't think that X.org would allow an application to take "total control". However you might want to use Java bindings for SDL for example.

---

