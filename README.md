# AltTagGen
Alt Tag Generation Project conducted by Alexis Kaufman, Shreya Kuntumalla, Jake Lee, and Jwalin Shah

@ University of Texas at Dallas

CS 4375.001

## References
- https://www.tensorflow.org/tutorials/images/cnn
- https://towardsdatascience.com/tensorflow-vs-pytorch-convolutional-neural-networks-cnn-dd9ca6ddafce
- https://medium.com/@nicolafan/end-to-end-implementation-of-an-image-caption-generator-with-cnn-and-rnn-using-tensorflow-and-keras-589f8ddea32b

- (Demo) https://www.tensorflow.org/text/tutorials/image_captioning
- (Gooel Colab) https://colab.research.google.com/drive/1qGrUQ28kcYZ19mkNOOvoBmgYWTwwdwPx?usp=sharing

## Alt Tag Generation for Improved Web Accessibility
This project tackles the challenge of generating "alt" tags for images that lack them, specifically aiming to improve web accessibility for users with visual impairments.

## Approach
The model processes the surrounding context of an image to understand its content. This context includes the caption, headings, and image title. Additionally, it downloads the image and generates a caption using TensorFlow, which is then used as a feature for the final model.

## Implementation Details
The implementation can be broken down into several steps:

- Pre-processing Data: This involves extracting relevant features from the dataset, including captions, headings, parsed titles, and URLs for image download (extracted from Wikimedia sources). It also performs checks to ensure the usability of existing "alt" tags within the data.
- Generating Captions: A TensorFlow model trained on a separate dataset is used to generate captions for the downloaded images. This adds another layer of information for the final model.
- Combining Features: Features from various sources, including pre-processed data and generated captions, are combined to create a comprehensive representation for each image.
Word2Vec Model: A Word2Vec model is used to convert the combined features into a semantic vector representation, allowing the model to understand the relationships between words within the context of the image.

Then the model was trained using Flickr8's dataset for further improvement in accuracy; also further analysed accuracy vs loss relationship

## Evaluation and Results
The model's performance was evaluated using the BLEU score, a metric that compares generated captions against ground truth "alt" tags. While the results showed promise, the model's BLEU score fell short of the established BLIP model, indicating room for improvement.

Further qualitative analysis revealed several challenges:

- Errors in generated captions by the TensorFlow model.
- Limited training data impacting the model's ability to learn a wider range of vocabulary.
- Implementation complexities related to combining features from different sources.
- Common issues like repeated words within generated alt tags.
  
## Future Work
Several avenues for future research can address the identified limitations:

- Retraining the TensorFlow model with a larger and more diverse dataset to improve its vocabulary and caption generation accuracy.
- Exploring different word embedding techniques to capture semantic similarity more effectively.
- Utilizing a language model to refine the generated alt tags and ensure they are grammatically correct and syntactically sound.
- Leveraging more powerful hardware for handling larger datasets during training.
- Integrating additional tools like sentiment analysis to provide more nuanced alt tag descriptions.
