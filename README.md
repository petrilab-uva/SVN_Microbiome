# SVN_Microbiome
Repository for analysis of Bangladeshi samples from first-trimester pregnant women. In this analysis we analyzed the gut microbiome, plasma inflammatory markers, micronutrient concentrations, and positivity for aEPEC and their relation to the birth outcome small vulnerable newborns (SVN).



## Paper: 

McMillan et al. First-trimester maternal gut microbiome and small vulnerable newborns: a prospective cohort study. 2026. BJOG


Preprint: McMillan, R. et al. The first-trimester maternal gut microbiome is a predictor of the birth of small vulnerable newborns in rural Bangladesh: A prospective cohort study. Preprint at https://doi.org/10.22541/au.176644102.26742975/v1 (2025).

## Summary of project:
Objectives: To investigate the relationship between the first trimester microbiome and small vulnerable newborns (SVN). 
Setting: Rural low, middle-income country: Bangladesh 

Population: 213 pregnant women were enrolled during the first trimester of pregnancy as part of the NICHD Global Network for Women’s and Children’s Health registry, Bangladesh. 

Methods: Blood and stool samples were collected at enrollment and birth outcomes within 72 hours of delivery. Using random forest machine learning models, whether the first-trimester maternal microbiome predicted SVN was evaluated. Main outcome measures: Small vulnerable newborns (born preterm, low birth weight, or small for gestational age). 

Results: The birth outcome SVN could be discriminated from non-SVN using a microbiome-trained random forest model (AUC = 0.653, 95% CI 0.518-0.789) supporting that the microbiome can influence gestation and fetal development. The microbiome also predicted the inflammatory markers plasma alpha-1-acid glycoprotein and fecal calprotectin (AUC = 0.742, 95% CI: 0.616-0.868 and AUC = 0.793, 95% CI: 0.680-0.905, respectively), while micronutrient concentrations, anemia, C-reactive protein, and the presence of atypical Enteropathogenic E. coli were not reliably predicted. Connecting inflammation to SVN, it was found that higher α-1-acid glycoprotein was significantly associated with SVN (logistic regression: aOR = 1.98; 95% CI: 1.04-3.85) whereas no significant association between calprotectin and SVN was observed. 


## Data access: 
Gut microbiome 16S fastq files available at: https://www.ncbi.nlm.nih.gov/sra/PRJNA1499123
BioProject accession number: PRJNA1499123


Meta data: 
Located on Github
Meta data file 1: raw meta data
SVN_Microbiome_meta-data_curated
Meta data file 2: processed meta data with derived variables
SVN_Microbiome_meta-data_curated_full
Data dictionary: 
SVN_Microbiome_data-dictionary


## R files:
Many steps in the analysis process require previous scripts to be run. Some editing of the scripts may be necessary depending on where files are located. 


Some processes require large amounts of RAM to run efficiently. Memory clearing steps have been included to reduce the needed memory. 

These are in the Markdown format. 


### File and explanation: 


SVN_Microbiome_Data-organization_deriving-variables
	Process of deriving meta data and birth outcome variables. This will use the “SVN_Microbiome_meta-data_curated” and yields the “SVN_Microbiome_meta-data_curated_full” file. 



SVN_Microbiome_Dada2_Batches1-4
	Dada2 pipeline for each batch of sequencing. Uses fastq files (see above). Some reorganization of fastq files may be necessary.



SVN_Microbiome_Phyloseq_all-batches
	Creation of a phyloseq object from output of Dada2 pipeline. Includes filtering of samples with low sequencing quality.



SVN_Microbiome_cross_table
	Cross table of SVN vs Healthy. Uses history from “SVN_Microbiome_Phyloseq_all-batches”



SVN_Microbiome_cross_table_excluded
	Cross table of included vs excluded samples. Uses history from “SVN_Microbiome_Phyloseq_all-batches”



SVN_Microbiome_diversity
	Alpha diversity, beta diversity, and phylum composition of microbiomes for SVN vs healthy. Uses history from “SVN_Microbiome_Phyloseq_all-batches”



SVN_Microbiome_logistic_regression
	Logistic regression of AGP or calprotectin and its association with SVN. Uses history from “SVN_Microbiome_Phyloseq_all-batches”



SVN_Microbiome_Random-Forests
	Random forests predicting SVN, and maternal variables from ASVs. Uses history from “SVN_Microbiome_Phyloseq_all-batches”. Each random forest model can be run independently from the others. Seed repeatedly set so that each section can be edited and run without altering others. 


SVN_Microbiome_paper_figures
	Formation of figures. Output from each corresponding R file needed for figure generation. 	
