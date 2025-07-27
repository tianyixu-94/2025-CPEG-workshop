# Palaeoverse Workshop Template

Tianyi Xu 07272025
University of Zurich

## Purpose

The aim of this template is to provide a set structure for the organisation of content and materials for workshops run by [Palaeoverse](https://palaeoverse.org). It is established for the internal Palaeoverse team and is therefore specific to our needs. However, if useful, anyone is free to download or reuse the template for their own purposes.

## Instructions

So, we're doing another workshop are we!? Follow this helpful checklist to get started with this template.

1. On the main page of the repository, click 'Use this template' (top right) and select 'Create a new repository'.
2. Enter a suitable repository name for the workshop, including the year and place/event (e.g. 2023-UCL-workshop, 2024-NAPC-workshop).
3. You are now ready to start creating your workshop content and materials. Start by updating the `README.md` file in the repository. You may wish to include information about the workshop (e.g. who it is run by, where and when, funding support, etc) and archiving information ([see below](#archiving)).
4. At this point you should edit the `index.qmd` in the top-level of the directory. There is placeholder text in the file, so just update accordingly! Note that whatever `title` you list in the header will be used for the navigation menu in the [workshop website](https://workshop.palaeoverse.org). The `order` attribute should be updated to place this workshop in the desired location in the navigation menu. The oldest workshop (UCL 2023) has `order: 99`, the next oldest workshop (NAPC 2024) has `order: 98`, etc. **You should assign your workshop with the highest `order` value less than 100 that has yet to be used (you can check the files in the [workshop website repository](https://github.com/palaeoverse/workshop) if counting is too hard).**
5. You can now prepare your course materials. Each unit of the workshop should have a designated folder (with an informative name). Placeholder folders have been included (e.g. `01_UNIT_NAME`), which you can rename, delete, or add to as you please. Within each unit folder, you should have an `index.qmd` file. This is the landing file you should populate for the given unit. As with the root `index.qmd` file, the `title` in this file will be used in the navigation menu.
6. **In order to ensure that the units are listed in the desired order in the navigation menu, the `order` attribute in the YAML of each `index.qmd` file should be updated to reflect the desired order of the units (e.g. the `index.qmd` file in the first unit should have `order: 1`, the `index.qmd` file in the second unit should have `order: 2`, etc).**
7. (optional) Within each unit folder, you can also have other .qmd files if you need to organize your content across multiple pages. You should again use the `order` attribute to determine the order of these pages in the navigation menu. You are welcome to also include other materials in these unit folders, including, but not limited to, images, scripts, and data files. You can structure your materials as you please, but in general, we recommend being organised - this means having a dedicated folder structure such as `materials/data`. **When linking between pages, linking to other materials, or including images, make sure to use relative paths instead of absolute paths.** You may also use full URLs if linking to external materials or including external images.

## Deploying to the Palaeoverse Workshop Website

When you are happy with the content in your individual workshop repository, you'll want to deploy it to the [workshop website](https://workshop.palaeoverse.org). Fortunately for you, we've developed a GitHub Actions [workflow](https://github.com/palaeoverse/workshop-template/blob/main/.github/workflows/copy.yml) that will automatically copy your materials into our general [workshop website repository](https://github.com/palaeoverse/workshop) and a separate Github Actions [workflow](https://github.com/palaeoverse/workshop/blob/main/.github/workflows/publish.yml) that will then render the new files and regenerate the website and host it on GitHub Pages.

In order to start this syncing process, you will need to add a super secret SSH key to your repository settings. You can follow these steps to add the key as a repository secret:

1. While looking at the landing page for your GitHub repository, click on the 'Settings' tab at the top of the page (settings for the repository, not the account settings; it should have a gear icon). If you don't see this tab, you'll need to get someone with admin access to help.
2. On the left-hand side pane click on 'Secrets and variables' and then on 'Actions'.
3. Click on the green 'New repository secret' button.
4. Under 'Name' put 'SSH_DEPLOY_KEY'. Under 'Secret' put the contents of the `id_github_workshop` file (it's located in the Palaeoverse Google Drive in the Workshop folder).
5. Click the green 'Add secret' button.
6. Click the 'Actions' tab at the top (it has a play button icon).
7. Click on the most recent (closest to the top) workflow run, then on the top right, click the 'Rerun all jobs' button. If a prompt appears, click the green 'Rerun all jobs' button.

Now sit back and relax while all of your hard work is copied to the website repository and the [workshop website](https://workshop.palaeoverse.org) is updated! Once the SSH key is set, any time you update materials in your repository, the workflows will again run and automatically update the workshop website. Once you push your changes to GitHub, the full website updating and rendering process should normally take ~5-10 minutes.

**Note: We strongly recommend that you wait to add this SSH key secret to your repository until you are somewhat ready for your materials to be published to the website. Once the secret is in place, all changes will be copied and published automatically to the public website.**

## Archiving

We strongly recommend that you archive your workshop materials. Archiving should be done via continuous integration with Zenodo, implemented through version controlled releases (a manual process when all content has been prepared). You can follow the [instructions here](https://docs.github.com/en/repositories/archiving-a-github-repository/referencing-and-citing-content) to link your GitHub repository to Zenodo and set up automatic archiving whenever a new release is created.

## Folder structure and content

```bash
├── workshop-template
│   ├── README.md
│   ├── index.qmd
│   ├── 01_UNIT_NAME
│   │   ├── index.qmd
│   ├── 02_UNIT_NAME
│   │   ├── index.qmd
│   ├── 03_UNIT_NAME
│   │   ├── index.qmd
│   ├── 04_UNIT_NAME
│   │   ├── index.qmd
│   ├── 05_UNIT_NAME
│   │   ├── index.qmd
│   ├── images
│   │   ├── logo.png
├── LICENSE
├── workshop.Rproj
├── .github
│   │   ├── workflows
│   │   │   ├── quarto-publish.yml
└── .gitignore
```

![](images/logo.png)
