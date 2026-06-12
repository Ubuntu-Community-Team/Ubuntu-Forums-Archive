---
title: "Piping output from ngram-count to ngram in the SRILM"
date: 2010-02-14
forum: Programming Talk
---

### Post by aonaran on 2010-02-14
Hi,

I've just started to use the SRI International Language Modeling toolkit (SRILM). I'd like to use its 'ngram-count' program to create a trigram language model (LM) on a corpus, and then use its 'ngram' program to evaluate the perplexity of the language model. However, I can't seem to pipe the output from 'ngram-count' to 'ngram' to successfully evaluate the LM.

A .deb for the SRILM can be obtained from the Ubuntu NLP Repository [here]("http://cl.aist-nara.ac.jp/~eric-n/ubuntu-nlp/dists/jaunty/nlp/").

The command for 'ngram-corpus' I'm using is
[FONT="Courier New"]ngram-count -text TRAINDATA -lm LM[/FONT]

The command for 'ngram' I'm using is
[FONT="Courier New"]ngram -lm LM -ppl TESTDATA -debug 2
[/FONT]

Any help with this issue is greatly appreciated.

---

