---
title: "Gaussian smoothing"
date: 2009-08-09
forum: Programming Talk
---

### Post by PaulM1985 on 2009-08-09
Hi

I am looking at writing a program that will deal with scaling down of images to make them a smaller file size and then move onto looking at stitching images together.

I have pretty much sorted the image scaling using a Gaussian distribution but I have a problem with it on one occasion and I am not sure what it is exactly.

I am iterating over a 12 x 12 array and have a variance of 0.2.  When I sum up all the Gaussian values I have 1.07.  This is greater than 1 and so when I use this on colours that are near to white (255)  I get values greater that 255 and so get an error because my colour is out of the [1-255] bounds.

My function for the distribution is this:
```

public static double getGaussian(int i, int j, double aSigmaSquared)
	{
        double sigmaSquared = aSigmaSquared;
        return ((1 / (2 * Math.PI * sigmaSquared)) * Math.exp(-(Math.pow(i, 2) + Math.pow(j, 2)) / (2 * sigmaSquared)));
	}

```

It would be much appreciated if anyone could spot what I have done wrong here because at the moment I am having to loop through the distribution values first to find the overall output for the gaussian distribution and use it to scale down the colours (so I stay in the range 1-255).

Paul

---

### Post by TheStatsMan on 2009-08-09
> **PaulM1985 said:**
> Hi

I am looking at writing a program that will deal with scaling down of images to make them a smaller file size and then move onto looking at stitching images together.

I have pretty much sorted the image scaling using a Gaussian distribution but I have a problem with it on one occasion and I am not sure what it is exactly.

I am iterating over a 12 x 12 array and have a variance of 0.2.  When I sum up all the Gaussian values I have 1.07.  This is greater than 1 and so when I use this on colours that are near to white (255)  I get values greater that 255 and so get an error because my colour is out of the [1-255] bounds.

My function for the distribution is this:
```

public static double getGaussian(int i, int j, double aSigmaSquared)
    {
        double sigmaSquared = aSigmaSquared;
        return ((1 / (2 * Math.PI * sigmaSquared)) * Math.exp(-(Math.pow(i, 2) + Math.pow(j, 2)) / (2 * sigmaSquared)));
    }

```It would be much appreciated if anyone could spot what I have done wrong here because at the moment I am having to loop through the distribution values first to find the overall output for the gaussian distribution and use it to scale down the colours (so I stay in the range 1-255).

Paul

Try

[PHP]
(1.0 / (2.0 * Math.PI * sigmaSquared))
[/PHP]

The code is a little strange. What is the point of this for instance

[PHP]double sigmaSquared = aSigmaSquared;[/PHP]

---

### Post by PaulM1985 on 2009-08-09
Im still getting the same result.

The sigmaSquare = aSigmaSquared is in from when I was developing it initially.  I was going to have a gaussian class and then realised i didnt really need a class for it.

After changing the 1 to 1.0 and 2 to 2.0 I still get the same result.

Paul

---

### Post by MadCow108 on 2009-08-09
you get numerical errors because of the low sigma
you need to increase the stepsize or preevaluate and normalize.
the latter is more reliable and faster as constantly evaluating a gauss is rather expensive

---

### Post by PaulM1985 on 2009-08-09
Thanks

I thought that was probably it but wanted to check that I wasn't doing anything wrong in the calculation.

I am going to use average for sigma less than 1 and hopefully this will speed it up a bit.

Thanks again

Paul

---

### Post by TheStatsMan on 2009-08-10
The easiest way to avoid numerical errors is to use the log of the probability distribution. I do almost all calculations involving probability distributions this way. Note that care needs to be taken with the sum. Suppose x~i.i.d.N(mu, sigsq), and you want the log(x(1)+x(2)+x(3)) then calculate
 [PHP]lnx=-0.5*(log(2*pi*sigsq)+(x-mu)^2/sigsq);[/PHP] for i=1,2,3 then calculate maxlnx = maximum of lnx(1), lnx(2), lnx(3), then

[PHP]log(x(1)+x(2)+x(3))=log(exp(lnx(1)-maxln)+exp(lnx(2)-maxln)+exp(lnx(3)-maxln))+maxln[/PHP]

---

