---
title: "ImageIO.read of InputStream fails"
date: 2011-07-29
forum: Programming Talk
---

### Post by dmatlock on 2011-07-29
I have an issue which is only appearing on ubuntu deployments. What happens is that I pass in image data in byte[] format. I run the following code...


    public byte[] resizeImage(byte[] image, String type, int maxWidth, int maxHeight) {
            InputStream in = new ByteArrayInputStream(image);
            BufferedImage originalImage = ImageIO.read(in);


The ImageIO.read throws an exception

Exception:javax.imageio.IIOException: Can't create cache file! at javax.imageio.ImageIO.createImageInputStream(ImageIO.java:351) at javax.imageio.ImageIO.read(ImageIO.java:1341)


Any ideas?

---

### Post by PaulM1985 on 2011-07-29
Which JVM are you using, openJDK or Java Sun?  If it is working fine on Windows I would assume that you are using Sun on Windows and openJDK on Ubuntu (since I am fairly sure openJDK is the default).

Paul

---

### Post by dmatlock on 2011-08-01
That was the issue.

We reloaded Ubuntu OS, then manually installed Sun Java, then our application. The error disappeared.

Thanks for the quick answer!

---

