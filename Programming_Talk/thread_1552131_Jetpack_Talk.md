---
title: "Jetpack Talk"
date: 2010-08-12
forum: Programming Talk
---

### Post by lovinglinux on 2010-08-12
This thread started with a discussion with SilverWave on [his thread about Firefox install]("http://ubuntuforums.org/showthread.php?t=1352580") using his PPA repositories, but since the subject is completely off topic for that place and the discussion is not going to end soon, I decided to ask a moderator to move it here.

The thread started with SilverWave talking about the problem of extensions incompatibilities with Firefox 4.

> **SilverWave said:**
> Oh well hopefully with Jetpack, eventually, this will be a thing of the past!

Jetpack is the next generation of Firefox extension framework, which is similar to Google Chrome extension model in many ways, but with the addition of several clever features and tools. Basically, it's Google Chrome extensions with steroids on top of Firefox's powerful extension API.

Below you can find some interesting resources, fetched from the initial discussion, that allowed me to understand it a little better:

[http://vimeo.com/10011379](http://vimeo.com/10011379)
[http://vimeo.com/7660200](http://vimeo.com/7660200)
[https://jetpack.mozillalabs.com/faq.html](https://jetpack.mozillalabs.com/faq.html)

If you want to start developing Jetpack extensions, you don't need to download the SDK. You can use the online [Add-on Builder]("https://builder.mozillalabs.com/"), which is looking really great so far. Nevertheless, you might want to take a look at the [SDK documentation]("https://jetpack.mozillalabs.com/sdk/0.6/docs/#guide/getting-started") to understand how Jetpack works.

**Links:**

Jetpack Home: [https://jetpack.mozillalabs.com/](https://jetpack.mozillalabs.com/)
Add-ons Builder: [https://builder.mozillalabs.com/](https://builder.mozillalabs.com/)
Discussion Group: [http://groups.google.com/group/mozilla-labs-jetpack](http://groups.google.com/group/mozilla-labs-jetpack)
Wiki: [https://wiki.mozilla.org/Labs/Jetpack](https://wiki.mozilla.org/Labs/Jetpack)
Other Resources: [http://groups.google.com/group/mozilla-labs-jetpack/web/resource-links](http://groups.google.com/group/mozilla-labs-jetpack/web/resource-links)

---

### Post by SilverWave on 2010-08-12
> **lovinglinux said:**
> 

I haven't tried Jetpack recently, but as far as I could understand, it is similar to Chrome extensions. IMO, the regular extension API is too powerful and popular to be replaced.

Well the feeling I have got from watching the posts of the developers is that they will try to create a Jetpack framework that replaces the old extension system.

There will target the low hanging fruit first, possibly 70% of extensions could be converted to use the new JetPack in the short to medium term...

Then they would need to find a way to extend JetPack to cater for the extensions that need deeper integration with Firefox.

Seems a good idea to me if they can pull it off.

And even if only 50% of extensions were converted to JetPack that would be a huge win.
Once they work on JetPack they are guaranteed to work on future versions of Firefox!
No more Upgraders Dilemma.

:-)

---

### Post by lovinglinux on 2010-08-12
> **SilverWave said:**
> Well the feeling I have got from watching the posts of the developers is that they will try to create a Jetpack framework that replaces the old extension system.

There will target the low hanging fruit first, possibly 70% of extensions could be converted to use the new JetPack in the short to medium term...

Then they would need to find a way to extend JetPack to cater for the extensions that need deeper integration with Firefox.

Seems a good idea to me if they can pull it off.

And even if only 50% of extensions were converted to JetPack that would be a huge win.
Once they work on JetPack they are guaranteed to work on future versions of Firefox!
No more Upgraders Dilemma.

:-)

As long as there is no feature loss, then I wouldn't mind to port my extensions to Jetpack, specially if that means I don't have to upgrade them whenever a major version of Firefox is released.

---

### Post by lovinglinux on 2010-08-12
I finally understood the relationship between Jetpack and extensions, after watching [this video]("http://vimeo.com/10011379"). It is really interesting. 

From what I could understand, the Jetpack SDK is a set of tools that allow you to build your extension into a bundled xpi package, that will include the necessary API code. So instead of putting the the entire API in Firefox, which leads to the upgrade drama, each Jetpack extension would have it's own updated API sets. 

When a new major version of Firefox is released, you can just load your jetpack into the new SDK and rebuild the extension, without the need to update the code. If you need to distribute a security patch for your add-on, then you could simply upload the new jepack and AMO would take care of inserting it into your xpi package and push the update to users.

> **lovinglinux said:**
> I don't think so. I haven't tried Jetpack recently, but as far as I could understand, it is similar to Chrome extensions. IMO, the regular extension API is too powerful and popular to be replaced.

I guess I was wrong :)

After watching the video above and reading the [Jetpack faq]("https://jetpack.mozillalabs.com/faq.html"), I must agree with you. 

> **SilverWave said:**
> Then they would need to find a way to extend JetPack to cater for the extensions that need deeper integration with Firefox.

Looks like we will be able to extend it ourselves. If an extension we want to write cannot be developed with Jetpack SDK, we can build a new API to make it work and share this API with other developers. How hard would that be, I have no idea, but seems a very clever thing.

This is going to be very interesting. I think I'm going to download the SDK and try it :)

---

### Post by SilverWave on 2010-08-13
> **lovinglinux said:**
> I finally understood the relationship between Jetpack and extensions, after watching [this video]("http://vimeo.com/10011379"). It is really interesting. 


Great video. On the same site I found this one regarding security...

[http://vimeo.com/7660200](http://vimeo.com/7660200)

Looks like they have built on some good ideas in Android but added reviewers and Red Amber Green warnings.

Cool :-)

---

### Post by lovinglinux on 2010-08-13
> **SilverWave said:**
> Great video. On the same site I found this one regarding security...

[http://vimeo.com/7660200](http://vimeo.com/7660200)

Looks like they have built on some good ideas in Android but added reviewers and Red Amber Green warnings.

Cool :-)

Check out [this video]("http://www.youtube.com/watch?v=DO-nzPqhdXw"). Jetpack uses the same concept of [least privilege]("http://en.wikipedia.org/wiki/Least_privilege"), but with a better implementation in my opinion. 

The addition of the review process is something I consider essential. Google has really screwed on this department.

BTW, I have sent a message to Jetpack Discussion Group and I was informed XUL extensions (the regular ones) are not going anywhere. Jetpack is not a replacement, but an addition. XUL will still be necessary for complex extensions. I think this is great, because we can have the best of both worlds.

---

### Post by SilverWave on 2010-08-13
> **lovinglinux said:**
> ...BTW, I have sent a message to Jetpack Discussion Group and I was informed XUL extensions (the regular ones) are not going anywhere. Jetpack is not a replacement, but an addition. XUL will still be necessary for complex extensions. I think this is great, because we can have the best of both worlds.

I think it will depend on how successfully Jetpack is TBH.

If it gets a lot of take up... well we will see ;-)

---

