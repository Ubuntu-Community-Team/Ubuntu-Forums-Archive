---
title: "Getting started with cuda, what card, etc?"
date: 2011-02-12
forum: Programming Talk
---

### Post by afireohno on 2011-02-12
I'm thinking of building a machine to take advantage of the increased number crunching abilities of a GPU. I was wondering if people might be willing to share experiences and suggestions on the subject as I'd like to avoid as many headaches as possible. Particularly I'm interested in what I should look at for a card with good linux support. I've never been a game player, so Gaphics cards are uncharted territory for me.

thanks

---

### Post by talonmies on 2011-02-12
If you want to use CUDA, you need an NVIDIA card. Linux support is pretty uniform and good across all current cards with recent drivers. I would strongly recommend buying a "Fermi" architecture GPU, just because of the programming benefits they bring over older architectures.

What card you choose probably comes down to whether double precision floating point performance is important to you or not, and if it is, exactly how important.

---

### Post by afireohno on 2011-02-12
Thanks. Keywords like "fermi" are exactly the type of info I was looking for.
That being said I don't actually plan on digging into the actual nuts and bolts of CUDA programming itself and will be mostly using libraries (theano, cudamat, gnumpy) for linear algebra routines.
Speed and memory (ability to work with large matrices) are infinitely more important than precision to me.

---

