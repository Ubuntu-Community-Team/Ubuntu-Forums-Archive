---
title: "Neural network gradient by backpropagation"
date: 2008-12-06
forum: Programming Talk
---

### Post by CptPicard on 2008-12-06
Has anyone here been playing with backprop? I have been puzzling over an adaptation of the procedure for a long time now and am feeling a little insecure in my understanding...

Now, in traditional backpropagation we work with an error function, where the output unit gets a local relative error computed which is then pushed back over the network and divided over the links as we go. So far so good; we get a gradient for minimizing our error function.

Now, I also come across these claims that backprop lets us also compute a gradient for the actual *value* of the function represented by the NN. Now, all the implementations or accurate descriptions of the algorithm always work with the *error*, and it seems like this is left "as an exercise for the reader". :)

In particular, see here: [http://www.cs.ualberta.ca/~sutton/book/11/node2.html](http://www.cs.ualberta.ca/~sutton/book/11/node2.html)

[IMG]http://www.cs.ualberta.ca/~sutton/book/11/img27.gif[/IMG]

> 
The gradient in this equation can be computed efficiently by the backpropagation procedure. 

Umm... ok. So how do we do that? :)

So far I've been working under the assumption that what I just do is that I try to replace the error with the value, so essentially the "local error" becomes 1 at the output node, and then this "effect" is pushed back analogously to the usual backprop algorithm... am I totally mistaken or is this how it's supposed to be done?

---

### Post by nvteighen on 2008-12-06
> **CptPicard said:**
> Has anyone here been playing with backprop? I have been puzzling over an adaptation of the procedure for a long time now and am feeling a little insecure in my understanding...

Now, in traditional backpropagation we work with an error function, where the output unit gets a local relative error computed which is then pushed back over the network and divided over the links as we go. So far so good; we get a gradient for minimizing our error function.

Now, I also come across these claims that backprop lets us also compute a gradient for the actual *value* of the function represented by the NN. Now, all the implementations or accurate descriptions of the algorithm always work with the *error*, and it seems like this is left "as an exercise for the reader". :)

In particular, see here: [http://www.cs.ualberta.ca/~sutton/book/11/node2.html](http://www.cs.ualberta.ca/~sutton/book/11/node2.html)

[IMG]http://www.cs.ualberta.ca/~sutton/book/11/img27.gif[/IMG]



Umm... ok. So how do we do that? :)

So far I've been working under the assumption that what I just do is that I try to replace the error with the value, so essentially the "local error" becomes 1 at the output node, and then this "effect" is pushed back analogously to the usual backprop algorithm... am I totally mistaken or is this how it's supposed to be done?
... :p

---

### Post by CptPicard on 2008-12-06
> **nvteighen said:**
> ... :p

Come on now, I'm sure someone can help me out here ;)

---

### Post by jpkotta on 2008-12-06
I am by no means an expert in NN, but I saw them in an optimization theory class.  Backpropagation is efficient because it reuses values that were previously computed, and reuses them several times.  

In training the NN, we minimize the squared error of the output vs. desired output w.r.t. the inputs of the net.  We can use gradient descent algorithms to minimize the error because it is relatively easy to compute the gradient w.r.t. the weights.  It is also easy to compute the gradient w.r.t. the inputs, because they are essentially the same as the weights from a computing-derivatives perspective.  

Let the output be y, the inputs be x[i], the inputs to the y neuron from the last hidden layer be z[j], the weights for the y neuron be w[j], and the sigmoid-type function be phi().
```
y = phi(sum(w[j]z[j])) = phi(w.z)
```
'.' is the scalar (dot) product.

We want grad(y,x).  We need dy/dx[i] to compute this.
```
dy/dx[i] = phi'(w.z) w.dz/dx[i]
dz/dx[i] = [dz[0]/dx[i], dz[1]/dx[i], ...]
```
So now we need the derivative of each z[j] w.r.t. x[i].  Since each z[j] is the output of a neuron, the calculation looks very similar to the above for y, and we can proceed recursively until we get to the inputs.  

If there are several outputs, there is no such thing as the gradient of the output, because gradients are defined for scalar-valued functions only.  We could find a matrix of all the partial derivatives of y[k] w.r.t. x[i], which is called the Jacobian matrix, and is indeed useful for optimization.

---

### Post by CptPicard on 2008-12-07
Thanks... I guess I'll just do a derivation wrt weights and see what pops out. Interestingly though, now that I really think of it, Sutton's way of putting his equation is fairly easily transformable to the error-surface version that is usable in backprop as it's usually done...

---

### Post by jpkotta on 2008-12-07
I misunderstood the question.  You wanted grad(y,W), where W is a vector of *all* the weights.  It's very similar to what I outlined above, it's just that some elements of the gradient (e.g. the ones in w, the last set of weights) require fewer iterations than others (e.g. the ones for the inputs to the 1st hidden layer).  

```
if W[k] is w[i] then dy/dW[k] = phi'(w.z) z[i] and we are done
otherwise, 
    dy/dW[k] = phi'(w.z) w.dz/dW[k]
    dz/dW[k] = [dz[0]/dW[k], dz[1]/dW[k], ...]
```

Again, find grad(z[i],W[k]), which uses the same type of calculation.

---

### Post by CptPicard on 2008-12-07
> **jpkotta said:**
> I misunderstood the question.  You wanted grad(y,W), where W is a vector of *all* the weights.

Yup. That is, steepest growth direction of the value of the network inside the weight-space. Sutton uses that sort of formalizations for some reason in his temporal difference learning-stuff :)

Anyway, I just did the math for a simple network and yes, the structure is fairly straightforward. Still not quite sure how it ties in with the backpropagation, but at least I've got the math now which is all I need ;)

---

