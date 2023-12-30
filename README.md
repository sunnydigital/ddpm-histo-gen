# Denoising Diffusion Probabilistic Models for Synthetic Histopathologic Image Generation
## Author: Sunny Son

This repository is primarily for the Final Project for Computer Vision, CSCI-GA.2271 Fall 2022, the goal of which being to train two (unconditional) DDPMs on classed datasets of `cancerous` and `non_cancerous` images obtained from the Patch Camelyon dataset.

We then ablate the models through two algorithmic metrics of:

- SSIM (Structural Similarity) Index
- Maximum Likelihood (in practice minimizing the log likelihood)

to test for the parameters `schedule` ($\beta$ noise schedule to use) and `attention` (whether or not to use an attention mechanism)

The experimentation is broken up into Ablation and Training, where

- Ablation: Found in the folders `ablation_study`, is the notebook to attempt different neural network combinations, as well as the results of each combination (the last epoch) after being trained for 100 epochs.

    - Usually, data would be downloaded in the `data` folder, however given its size, GitHub was unable to take the files

- The main Experiment: Two separate models trained under two separare notebooks, `ddpm_cancerous` and `ddpm_non-cancerous` which adds the feature of training where would else be left off (or training ended early), due to potential bugs or usage limits implemented when training on Google Colab.

There is much to do, and will be outlined here:

- [ ] Create a combined, **conditional** DDPM model to handle both input classes of cancerous and non-cancerous images.
- [ ] Add a feature in the main `DiffusionModel` class allowing for the specification of a `dim_mults` parameter to define the channel number at each layer and number of layers to use
- [ ] Increasing the input image size to 96x96px
- [ ] Allowing for training in parallel on multiple GPUs using Kubernetes

For now, enjoy these reverse diffusion images!

(Can *YOU* guess which ones are `cancerous` and which are `non_cancerous`?)

<p align="center">
    <img src="https://github.com/sunnydigital/cv-f22/blob/main/images/gifs/cosine_beta_schedule-no_attention05-interval10.gif" alt="Reverse Diffusion 1" width="49.7%"> <img src="https://github.com/sunnydigital/cv-f22/blob/main/images/gifs/cosine_beta_schedule-no_attention26-interval10.gif" alt="Reverse Diffusion 2" width="49.7%">
    <img src="https://github.com/sunnydigital/cv-f22/blob/main/images/gifs/cosine_beta_schedule-no_attention43-interval10.gif" alt="Reverse Diffusion 3" width="49.7%"> <img src="https://github.com/sunnydigital/cv-f22/blob/main/images/gifs/cosine_beta_schedule-no_attention47-interval10.gif" alt="Reverse Diffusion 4" width="49.7%">
</p>

These images awere generated using the combination of `cosine_beta_schedule` and `no_attention`, as through our ablation study, was shown to be the best combination of schedule/attention mechanism.
