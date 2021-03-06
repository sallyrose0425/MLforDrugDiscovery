# MLforDrugDiscovery

This document contains instructions for running all scripts in this repository to reproduce and run your own analysis to use machine learning to combine biomoleculer simulation data and cheminformatics and bioinformatics data for drug discovery models.

1. Obtain input data for project.
  * Protein structures: Every protein must have a structure (x,y,z coordinates of all atoms in the protein in PDB file format). Check the database in which you are getting data and the Protein Data Bank. If no experimental structure, or no full structure, homology modeling may be used.
  * Obtain known active (binding or positive class) compounds and decoy (non-binding or negative class compounds). Resources such as the Directory of Useful Decoys (and enhanced version) provide both sets for you. Databases like BindingDB can also be used to get active compounds. If no decoy compounds are provided, DUD-e provides their decoy generator.
2. Generate all features and parse output
* Protein Descriptors (Sequence) 
  * Get the human canonical sequence for each protein from UnitProt. 
  * Submit to three different: ExPasy, Porter & PaleAle 4.0, and PROFEAT – Protein Feature Server. 
* Protein Descriptors (Structural) 
  * Submit PDB file to Coach and 2struc. 
* Pocket Descriptors 
  * Run PDB file through modified PRANK
* Drug Descriptors 
  * Run the compound library through the Dragon Software. Using dragon7gui, create a script for running from the command line by selecting File > scriptwizard. Run the script by calling $ dragon7shell -s script.drs
* Binding Descriptors 
  * Prepare all proteins and drug compounds for docking with VinaMPI
  * Perform docking with VinaMPI
  * Rerun results of the docking jobs using the “--score-only” option to collect the individual terms calculated in the scoring function
3. Do any preprocessing for the initial dataset
4. Partition compounds by Scaffold Splits generated by MoleculeNet
5. Generate training, testing, and validation sets
6. Feature selection and modeling
7. Visualization of features
