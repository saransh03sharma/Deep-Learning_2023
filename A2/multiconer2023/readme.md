
# MultiCoNER 2 Dataset

MultiCoNER 2 represents the shared Task 2 *"Multilingual Complex Named Entity Recognition (MultiCoNER 2)"* at SemEval2023. 

The task focused on fine-grained named entity recognition with noisy context and noisy entity surface forms (with noise being the typing errors specific to keyboard layouts on different languages). 

We released the __MultiCoNER 2__ dataset for 12 different languages (EN, DE, FR, ES, IT, PT, SV, UK, FA, ZH, BN, HI), as well as the multilingual set, which consists of a mix of monolingual instances from the respective 12 languages. 


## Files

**MultiCoNER 2** dataset contains a separate folder for each language (including the multilingual), e.g. *EN-English*. Within each folder you will find three separate files containing the data for *training/dev/test*. 

### Format
The data is in *CoNLL format* and additionally for each instance has its own metadata, which contains the instance ID, domain (i.e., the language of the data), and in case the instance contains any noise, it contains the tokens that are corrupted and their corresponding indexes. See an example below:

```
# id 15afb6d2-5558-4b45-8704-f32bab341832   domain=en corrupt=True  changed_tokens=[(thheon,theon)] changed_indexes=[16]
it _ _ O
has _ _ O
been _ _ O
argued _ _ O
that _ _ O
the _ _ O
book _ _ O
may _ _ O
have _ _ O
been _ _ O
compiled _ _ O
by _ _ O
the _ _ O
4th _ _ O
century _ _ O
mathematician _ _ O
thheon _ _ B-OtherPER
of _ _ I-OtherPER
alexandria _ _ I-OtherPER
. _ _ O
```

## Data Description

Each of the individual language contains three files, namely, *train, dev, test*. The different splits have varying number of instances. *Train* files typically contain around ~16k instances, whereas *dev* contain typically ~800 instances. On the other hand, *test* files contains ~250k instances, apart for the languages DE, HI, ZH, BN, which contain approximately 20k instances.

The reason for the larger test set size is to assess model generalizability when trained on the much smaller train sets. 

### Noisy Instances
In MultiCoNER 2 we additionally added noise to 30% of the instances on the test sets of EN, DE, IT, FR, ES, ZH, PT, SV. The noise was added to either context or entity tokens. The noise corresponds to typing errors based on the keyboard layout on the respective languages.  

The noisy instances allow us to assess how the models behave in such scenarios, and whether the noise in entity tokens has an impact on the NER performance.

## Data  Stats
![MultiCoNER 2 Data Stats](https://drive.google.com/uc?export=view&id=1QMz1_1giTL7F-sFslwwHUi7ssjza10VJ)

## MultiCoNER 2 Taxonomy
The MultiCoNER 2 uses a fine-grained named entity taxonomy, consisting of 6 coarse grained types, and with a total of 36 fine-grained types. The taxonomy is shown below:

![MultiCoNER 2 Taxonomy](https://drive.google.com/uc?export=view&id=197m--oogeh63gnUFgqU7hzAyIUE0V0u7)

Finally, the entities are annotated using the IOB format. e.g.: 
```
theon _ _ B-OtherPER
of _ _ I-OtherPER
alexandria _ _ I-OtherPER
```

## Data Download
The data can be download from the following public S3. Please use the following command to download the data:

``aws s3 cp --no-sign-request s3://multiconer/multiconer2023/ multiconer2023/ --recursive``