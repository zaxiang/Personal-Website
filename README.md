# ids721-indiv1

![pipeline status](https://gitlab.com/dukeaiml/IDS721/yx248-indiv1/badges/main/pipeline.svg)

[My Zola Web](https://yx248-indiv1-dukeaiml-ids721-0dbfac262998dd8f7067eb4b9326dbe700.gitlab.io/)

# Continuous Delivery of Personal Website

This project focuses on the creation and continuous delivery of a personal website. The website is built using Zola, a fast and efficient static site generator written in Rust. The goal is to automate the build and deployment process, allowing updates to be pushed live automatically with each commit to the main branch of the project's GitLab repository.

## Introduction

A personal website serves as a digital portfolio showcasing your work, skills, and professional identity. By leveraging Zola and continuous delivery principles, we can ensure that the website is always up-to-date with the latest content and changes.

### Why Zola?
- **Speed:** Zola generates pages at an incredibly fast rate, enhancing the development workflow.
- **Simplicity:** With Zola, you can manage your content without the overhead of databases or heavy frameworks.
- **Flexibility:** Zola supports Markdown for content creation, making it easier to write and maintain website content.


## Project Setup

## Installation of Zola on Ubuntu

1. Download Zola from the [official releases page](https://github.com/getzola/zola/releases). For example, use `zola-v0.18.0-x86_64-unknown-linux-gnu.tar.gz`.

2. Unzip the package:

```bash
tar -xzf zola-v0.18.0-x86_64-unknown-linux-gnu.tar.gz
```

3. Move Zola to the bin directory:

```bash
sudo mv zola /usr/local/bin
```

For more information, refer to the [Zola Official Documentation]().


## Initial Setup and Running Zola Server

- Initialize the project:

    ```bash
    zola init project_name
    ```

    The structure should looks like:

    ```bash
    project root
    ├── config.toml
    ├── content
    ├── sass
    ├── static
    ├── templates
    └── themes
    ```

- Build the project:

    ```bash
    zola build
    ```

- Run the server (default port is 1111):

   ```bash
   zola serve
   ```


## Theme Installation

1. Download your chosen theme to the `themes` directory.

2. Update the `theme` variable in the configuration file to match the name of your theme's directory (e.g., `themes/kita`).

 **Note:** Ensure the `theme` variable is at the top level of the `.toml` hierarchy, not nested under sections like `[extra]` or `[markdown]`.

3. Follow any additional configuration instructions provided in your theme's documentation.

## Theme Usage and Customization

- To use a theme, add the `extends` directive in your template HTML files. Modify the blocks to fit the theme's index.

- For further customization, you can either:
- Copy the index code from the theme to your `index.html` file, or
- Modify the theme files directly.

- Update the `config.toml` file in your project's root directory with the theme's `config.toml` settings. Customize these settings to suit your project's needs.


## Website Structure

In the header of the page template, you'll find `Home` and `Projects` buttons that enable easy navigation between the Home page and the Projects List page, allowing quick access to any section of the website.

### Home Page

- Overview of the IDS-721 course content.
![Home Page](homepage.png)

### Projects List Page

- Portfolio of IDS-721 course projects.
![Projects List Page](projectslistpage.png)

### Project Detail Page

- Detailed view of a selected project.
- Direct links to the corresponding Git repository.
- Back button to return to the project overview list.
![Project Detail Page](projectpage.png)


## Deployment to GitLab Pages

To deploy your Zola site on GitLab Pages, follow these steps:

1. **Create a `.gitlab-ci.yml` File:**
   Create a `.gitlab-ci.yml` file in the root of your repository. This file is used by GitLab CI/CD to manage your project's jobs.

2. **Configure the CI/CD Pipeline:**
   Add the following script to your `.gitlab-ci.yml` file:

   ```yaml
   image: "registry.gitlab.com/pages/hugo:latest"

   pages:
     script:
     - zola build
     artifacts:
       paths:
       - public
    ```

   This script tells GitLab to use a docker image with Zola installed, build your site with Zola, and then store the output in the `public` directory.
   Remember to chang the `value: ""` in `ZOLA_VERSION:` to `value: "0.18.0"`.

3. **Push to GitLab:**
   Commit and push this file to your GitLab repository.

4. **Check Pipeline Status:**
   After pushing, navigate to `CI/CD > Pipelines` in your GitLab repository to check the status of your pipeline. Once it's passed, your site is live.

5. **Accessing Your Site:**
   Your site will be available at `https://[username].gitlab.io/[repository-name]`, where `[username]` is your GitLab username, and `[repository-name]` is the name of your GitLab repository.

6. **Custom Domain (Optional):**
   If you wish to use a custom domain, refer to the [GitLab Pages Custom Domains documentation](https://docs.gitlab.com/ee/user/project/pages/custom_domains_ssl_tls_certification/index.html) for guidance.

For more detailed instructions and configurations, visit the [Zola documentation on GitLab Pages deployment](https://www.getzola.org/documentation/deployment/gitlab-pages/).

## Demo Video link
- [Youtube Link](https://youtu.be/_m8Q7Sda6BI)
