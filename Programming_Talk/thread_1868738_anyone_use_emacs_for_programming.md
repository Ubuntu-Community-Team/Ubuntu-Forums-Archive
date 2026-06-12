---
title: "anyone use emacs for programming?"
date: 2011-10-24
forum: Programming Talk
---

### Post by cortman on 2011-10-24
I'm new to it and it seems quite powerful, but takes a good bit of getting used to. Anyone still use it or write extensions for it?

---

### Post by Arndt on 2011-10-24
> **cortman said:**
> I'm new to it and it seems quite powerful, but takes a good bit of getting used to. Anyone still use it or write extensions for it?

Sure.

---

### Post by matthew.ball on 2011-10-24
Depending on what you're after, but still, more than likely (though I am not really a programmer, per se, I am fairly comfortable with emacs and do have *some* experience programming in it. I do however know that there are some emacs users around UF).

The default settings (in particular, the default key-bindings) are fairly archaic, but you can get rebind them to a more "reasonable" mapping relatively easily. If you don't like the emacs' default C-w/M-w and C-y cut/copy and paste combination (which seems to be a common problem) there are extensions such as [CuaMode]("http://www.emacswiki.org/emacs/CuaMode") which clean this up (moving cut to C-x, copy to C-c and paste to C-v, which is more "natural" these days). Really, you can change a lot of how emacs works by customising your .emacs file; there are a lot of extensions which come with emacs (the aforementioned CuaMode being one example, another very useful extension is [ido]("http://www.emacswiki.org/emacs/InteractivelyDoThings")) unfortunately, since it doesn't come with a preconfigured "dotfile", these extensions are not enabled by default, so unless you're prepared to do a fair bit of digging around (which can be very time-consuming) you might not notice all the extra power.

Then, what programming language are you interested in using? For a language like C, emacs is very well directed. For something like Java, many people would argue not (though, of course it *can* be done).

You can set-up most of the full-blown bells-and-whistles of a modern IDE with emacs - project management features, auto-complete, default templates, debugging, etc (really, depends on what you want, but bare a GUI-design feature, it most probably exists for emacs).

The emacs-lisp programming language is not too difficult to pick-up either, it's fairly straight-forward, even if you are coming to it with no knowledge of a lisp-like language. I have written a very simple mode for an ad-hoc programming language (nothing too impressive - mainly just syntax-highlighting and comint support for running the solver) and that was not very difficult at all.

---

### Post by cgroza on 2011-10-24
I use it for programming mainly because it is powerful and gives me access to man pages, IRC and shell in the same window.

---

### Post by NovaAesa on 2011-10-25
I used to use it (for about a year) but recently switched to Vim. There are still many people using it though, and people still writing scripts for it as well.

---

### Post by cortman on 2011-10-25
> **NovaAesa said:**
> I used to use it (for about a year) but recently switched to Vim. There are still many people using it though, and people still writing scripts for it as well.

So do you actually prefer Vim? I've used it some too, learned the basics of using it anyway, and the modal thing always was a little tough to get used to. It's handy to at least have a basic knowledge of it, I think, since the CLI version comes bundled with most distros.
Emacs looks like it'd have a lot of potential for a real power user. I mean, you can even get your mail on it! although how it would interact with POP, IMAP, and SMTP on web based mail servers I'm not sure.

---

### Post by nvteighen on 2011-10-25
I use it (well, I've been a bit inactive in programming these days because of work)... mainly because I'm a Lisper and SLIME rocks :)

---

### Post by sujoy on 2011-10-25
I use emacs for all sorts of text editing. (including programming of course)

Also as a file manager (dired) and for irc and mail :)

---

### Post by lykwydchykyn on 2011-10-25
I use it for programming and writing and just about anything else involving text.  Most of my programming is PHP and javascript, followed by python.

I don't think it's that hard to learn, it just something you can constantly get better at.  You learn new tricks and techniques, find new extensions, and get accustomed to doing things "the emacs way" little by little the longer you use it.  And you keep customizing it until it becomes pretty much form-fit to your work flow.

---

### Post by schauerlich on 2011-10-25
> **nvteighen said:**
> I use it (well, I've been a bit inactive in programming these days because of work)... mainly because I'm a Lisper and SLIME rocks :)

I started using emacs when I was introduced to Lisp. I used vi before when I had to, but preferred GUI editors. Now I pretty much use emacs any time I don't need a specific IDE, such as when doing Cocoa programming.

---

### Post by gnometorule on 2011-10-25
I've used it for many languages, currently mostly C. I don't see it go away. It seems VIM users are pretty fanatic about, probably for good reason, but I could never take to it. If you don't VIM, emacs is a great choice, after all these years; even if you use only 5% of its commands.

---

### Post by mikaelcrocker on 2011-10-25
I use emacs too, it's great, it recognizes a ton of languages and the like.

if you're doing any kind of scripting or interpreted languages it's works really well.  What kind of programming/scripting are you looking to do?

---

### Post by cortman on 2011-10-25
> **mikaelcrocker said:**
> I use emacs too, it's great, it recognizes a ton of languages and the like.

if you're doing any kind of scripting or interpreted languages it's works really well.  What kind of programming/scripting are you looking to do?

I'm currently learning to program in Java, and trying to learn basic bash shell scripting.

---

### Post by cortman on 2011-10-26
I have a quick question on emacs here too: I'm trying to edit my grub.cfg file with emacs -nw, and even though I give the command "sudo emacs -nw grub.cfg" emacs still opens the buffer in read-only. How can I get it out of read only?

---

### Post by matthew.ball on 2011-10-26
You run [FONT="Courier New"]C-x C-q[/FONT] (or [FONT="Courier New"]M-x toggle-read-only[/FONT]) to switch between "read-only" and "write" permissions.

---

### Post by cortman on 2011-10-26
> **matthew.ball said:**
> You run [FONT="Courier New"]C-x C-q[/FONT] (or [FONT="Courier New"]M-x toggle-read-only[/FONT]) to switch between "read-only" and "write" permissions.

Thanks!

---

### Post by ballantony on 2011-10-26
I use emacs for perl and the little bit of php I occasionally do. For Java (in which I do 99% of my programming) I use Netbeans.

I use emacs org mode for just about everything I can use it for:  planning, scheduling, keeping notes.

---

### Post by matthew.ball on 2011-10-26
> **cortman said:**
> Thanks!
No worries :)

---

