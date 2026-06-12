---
title: "C++: MagickImage to Qt Image conversion?"
date: 2016-07-12
forum: Programming Talk
---

### Post by fallenshadow on 2016-07-12
Hi all,

At the moment my application does a conversion every time we apply a filter. This seems to have a huge performance hit.

```


Magick::Image* fromQtImage(const QImage &image) const
    {
        // TODO: May need to convert images pixel by pixel.
        // Also need to take into account whether the image has an alpha channel or not.
        QByteArray byteArray;
        QBuffer buffer(&byteArray);
        buffer.open(QIODevice::WriteOnly);

        //Use raw format instead of JPG to avoid image format conversion and quality loss
        if (!image.save(&buffer, "PNG"))
            return 0;

        Magick::Blob blob(byteArray.data(), byteArray.length());
        return new Magick::Image(blob);
    }

    QImage toQtImage(Magick::Image *image)
    {
        Magick::Blob blob;
        image->write(&blob);

        QByteArray arr((char *)blob.data(), blob.length());
        QImage img;
        img.loadFromData(arr);

        return img;
    }

QImage FilterManager::oilPaint(const QImage &image)
{
    Magick::Image *magickImage = d->fromQtImage(image);
    magickImage->oilPaint();

    QImage modifiedImage = d->toQtImage(magickImage);
    delete magickImage;

    return modifiedImage;
}

```

Is there a better way to improve the performance here? Any ideas or suggestions appreciated.

---

