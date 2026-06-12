---
title: "Neural Nets in python"
date: 2009-05-20
forum: Programming Talk
---

### Post by Mickeysofine1972 on 2009-05-20
Hi guys

I've been messing with neural nets in python but can seem to egt any good examples of doing prediction of future values.

Does anyone know any good tutorials or even have any example code I can peek at?

Mike

---

### Post by kjohansen on 2009-05-20
Prediction is an easier step than training.

Are you using backpropagation for training or something else?  If you are using backpropagation for training, the first half of the training is the code you would use for prediction?  The intuition being that you "push" forward the example point, and then backpropagate the error.

There are lots of good books that have pseudo code that is helpful for any language.  MY favorite for introductory AI is "Artificial Intelligence a Modern Approach" by Russel and Norvig.


This is a snippet of C++ code I wrote:

[php]
std::vector<double> NeuralNetwork::Predict(std::vector<double> x)
{
    for (int j = 0; j < layers[0].num_nodes; j++)
    {
        layers[0].nodes[j].a = x[j];
    }

    for (int l = 1; l < num_layers; l++)
    {
        for (int i = 0; i < layers[l].num_nodes; i++)
        {
            double sum = 0.0;
            for (int j = 0; j < layers[l - 1].num_nodes; j++)
            {
                sum += layers[l].nodes[i].weights[j] * layers[l - 1].nodes[j].a;
            }
            sum += 1 * layers[l].nodes[i].bias_weight;
            layers[l].nodes[i].in = sum;
            layers[l].nodes[i].a = sigmoid(layers[l].nodes[i].in);
        }
    }


    std::vector<double> y_ret;
    for (int i = 0; i < num_output; i++)
    {
        y_ret.push_back(layers[num_layers - 1].nodes[i].a);
    }
    return y_ret;
}
[/php]

---

### Post by Mickeysofine1972 on 2009-05-20
Hi

Yes I'm using backprop to train but what i cant get my head around is once trained how to I ask the NN to generate a result for an unknown / predicted value.

After training, do just I give it a series of possible values until it says "yes thats a match"?

Mike

---

### Post by Mickeysofine1972 on 2009-05-20
> **kjohansen said:**
> Prediction is an easier step than training.

Are you using backpropagation for training or something else?  If you are using backpropagation for training, the first half of the training is the code you would use for prediction?  The intuition being that you "push" forward the example point, and then backpropagate the error.

There are lots of good books that have pseudo code that is helpful for any language.  MY favorite for introductory AI is "Artificial Intelligence a Modern Approach" by Russel and Norvig.


This is a snippet of C++ code I wrote:

[php]
std::vector<double> NeuralNetwork::Predict(std::vector<double> x)
{
    for (int j = 0; j < layers[0].num_nodes; j++)
    {
        layers[0].nodes[j].a = x[j];
    }

    for (int l = 1; l < num_layers; l++)
    {
        for (int i = 0; i < layers[l].num_nodes; i++)
        {
            double sum = 0.0;
            for (int j = 0; j < layers[l - 1].num_nodes; j++)
            {
                sum += layers[l].nodes[i].weights[j] * layers[l - 1].nodes[j].a;
            }
            sum += 1 * layers[l].nodes[i].bias_weight;
            layers[l].nodes[i].in = sum;
            layers[l].nodes[i].a = sigmoid(layers[l].nodes[i].in);
        }
    }


    std::vector<double> y_ret;
    for (int i = 0; i < num_output; i++)
    {
        y_ret.push_back(layers[num_layers - 1].nodes[i].a);
    }
    return y_ret;
}
[/php]

So how do I generate the arg to the function "[COLOR=Red]std::vector<double> x"?

[COLOR=Black]Mike[/COLOR]
[/COLOR]

---

### Post by Mickeysofine1972 on 2009-05-21
Given that we are forecasting unknown values how can you know what values to put into the function above?

Anyone care to explain how to generate those numbers? I understand the algorithm, its just not obvious where those values come from.

Mike

---

### Post by Mickeysofine1972 on 2009-05-21
Ok think I'm starting to get it!

If I supply a list of previous "real" values to this function the output should be the predicted value?

Mike

---

