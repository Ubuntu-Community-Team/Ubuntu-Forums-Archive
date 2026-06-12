---
title: "DSP: Spectrum with FFTW"
date: 2010-12-05
forum: Programming Talk
---

### Post by hush-hush on 2010-12-05
Hello,

I currently begin to study DSP, so my first step is to get the spectrum of a song.

I use FFmpeg to decode the file, and FFTW to do discrete fournier transform and get the spectrum.

My probleme is that I can't get the upper part of my spectrum (the hight frenquency).

here is my code:
This function is call with sample in data, data contain 2 channel.
So n_data the number of data in each channel, and total_size is equal to n_data * 2.
"update_spectrum" update the display.
And rdft_data_in/rdft_data_out/plan are static, the function is always call with the same len of data.
```

static int calc_audio(float *data, int n_data, int total_size)
{
    int i;

    if (!rdft_data_in)
    {
        rdft_data_in = fftw_malloc(sizeof(*rdft_data_in) * n_data);
        rdft_data_out = (fftw_complex*) fftw_malloc(sizeof(fftw_complex) * n_data);
        plan = fftw_plan_dft_r2c_1d(n_data, rdft_data_in, rdft_data_out,
                        FFTW_MEASURE | FFTW_DESTROY_INPUT);
    }

    for(i = 0; i < total_size; i += 2)
        rdft_data_in[i / 2] = (data[i] + data[i + 1]) * .5f;
    fftw_execute(plan);

    double *freq_data = calloc(n_data, sizeof(*freq_data));
    for (i = 0; i < n_data; i++) {
        float r1 = rdft_data_out[i][0];
        float i1 = rdft_data_out[i][1];

        freq_data[i] =  sqrt(sqrt(r1 * r1 + i1 * i1) / sqrt(n_data));
    }

    update_spectrum(freq_data, n_data);
    return 0;
}

```here is the song with audacity (we can see that the file is a mp3, the upper frequency are null)
[IMG]http://hush-hush.me/spectrum_auda.png[/IMG]

Here my result as you see it miss my the half of my spectrum and I can't understand why,
[IMG]http://hush-hush.me/spectrum_test.png[/IMG]


Thanks for your help !

---

