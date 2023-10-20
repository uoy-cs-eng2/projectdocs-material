# ProjectDocs Material

A domain-specific language (PDL) for modelling collaborative research projects and a generator that produces an [MkDocs Material](https://squidfunk.github.io/mkdocs-material/) website from a PDL model.

![](screenshots/light-theme.png)

## Running the Generator

To generate the website from the project model, you need to run `gradle run` from the `pdl` directory. The generator will produce an `mkdocs.yml` file in the `mkdocs` directory, as well as Markdown files for the different partners, work-packages and tasks of the project under `mkdocs/docs/`.

## Serving the Website

To serve the website, you need to run the following command from the `mkdocs` directory:

### Windows

```
docker run --rm -it -p 8000:8000 -v %cd%:/docs/ squidfunk/mkdocs-material
```

### Linux / Mac

```
docker run --rm -it -p 8000:8000 -v ${PWD}:/docs/ squidfunk/mkdocs-material
```

You can then access the generated site at http://localhost:8000.

## Advanced

Gradle supports the `--continuous` flag, which keeps the build alive and re-runs tasks when their inputs change. To try this out, run `gradle --continuous run` instead of `gradle run`, serve the website as shown above, then modify `project.flexmi` (e.g. change the title of the project) and then observe Gradle reacting to the change and regenerating the respective Markdown files from it automatically.
