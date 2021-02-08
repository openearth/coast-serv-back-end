# instructions on how to create docker container from files:
- From command line, navigate to the folder containing the docker files. Create tidal boundary condition docker image with:
```bash
docker build --tag fmtide:1.0 -f Dockerfile_tide .
```
- Create physical and chemical boundary condition docker image with:
```bash
docker build --tag fmphyschem:1.0 -f Dockerfile_physchem .
```
- Check that the images have successfully been created with:
```bash
docker images
```
This should give output similar to:
```bash
REPOSITORY               TAG                 IMAGE ID            CREATED              SIZE
fmphyschem               1.0                 d505ffe8f5b3        41 seconds ago       1.29GB
fmtide                   1.0                 de95bab22212        About a minute ago   1.29GB
```
- To save the created docker images as a .tar files, run:
```bash
docker image save --output fmphyschem.tar fmphyschem:1.0
```
and
```bash
docker image save --output fmtide.tar fmtide:1.0
```
## Usage
- If the images are not created yet, create it from the tar files with:
```bash
docker load --input .\fmphyschem.tar fmphyschem:1.0
```
and
```bash
docker load --input .\fmtide.tar fmtide:1.0
```
- To use the created docker container to convert CMEMS input into a format that DFlowFM can use, follow the instruction in the readme.md file
to run the test case on the P drive: p:\11203850-coastserv\06-Model\Full_workflow_images_and_testcases
