# European Commission Nexteuropa example project

<img align="left" width="180" src="https://ec.europa.eu/ec_portal/2016/images/logo/logo-splashpage.png" />

<p>This is an example project showcasing possible implementations to improve the inventory, documentation and workflow of projects within the European Commission domain. By making full use of Composer we can streamline projects to become a container for a large part of the inventory. The live site of this project is located at https://ec.europa.eu/</p>

## Concept

The idea of this example project is to allow non-developer roles such as project managers to change specific information within the code repository through a controled manner (a.k.a pull requests). By allowing them to change certain project information within the codebase the repository itself becomes the datasource for any third party that needs to work on the project. It allows the project to become fully independent and agnostic. The repository itself will become the main datasource for the inventory. Which means it becomes possible for multiple parties to include it in their own inventory. Essentially the code repository which also holds the build system will just have a set of build properties required depending on which services they are making use of.

By creating composer plugins implementing REST api's we can provide default AND custom reactions to the change of project information. The easiest to understand example for this is to allow a project manager to control access to any resources that their teammembers need in fulfilling their role requirements. The current ec-europa/oe-task-runner is the perfect candidate to provide this functionality.

## Use cases
* maintain your own list of resources to which project members should have access to
* generate useful documentation within the repository so all parties involved know the workflow
* onboarding a new developer triggers REST API callbacks to:
  * provide access to any resources required for the developer
  * send out notifications to added and removed developers
* onboarding a new webmaster triggers REST API callbacks to:
  * automatically create an account with the desired role on the website of the project
  * send out all project information to the webmaster that they need to manage the site
* anyone is able to automatically send out communications to all projects they have access to
* projects can require other composer plugins or packages to gain access to services:
  * code review service
  * deployment service
* projects can implement their own service if they are not able to rely on DIGIT's
  * still adhereing to DIGIT's workflow
  * able to change to DIGIT

## Advantages
* ultimate control still remains with the original owner of the code repository
* a project is automatically official when they receive a repository
* third parties can use their own dashboard and inventory
* workflow is truely transparent to everyone involved
* each project is able to setup their own services if they wish to
* switching service providers is possible without too much hassle (github, gitlab, stash)
* the service provider callback urls can target the website acceptance url that in it's turn can distirbute it to any service
* it is self-authenticating since we can make the acceptance url site the highest and only authority
* individual implementations can by sent back for contribution (PHPCS exclusions, custom build targets)

## Disadvantages
* secrets have to be sent through REST as the services are located within the project itself
* allowing multiple service provider implementations can create incompatibilities
* component based systems require more attention to maintenance
* using an acceptance url for REST api callbacks may break the development workflow when the distribution endpoint goes down

## Details

This section is not provided by composer.json but it could be provided by a composer plugin that automatically regenerates any extra information related to the project. A REST interface connecting the inventory dashboard with the git repository could be responsible for updating the documentation with the extra information that is not covered with the default composer.json.

* **Production**: https://ec.europa.eu/
* **Playground**: https://webgate.ec.europa.eu/playground-multisite/europaeu
* **Testing**: https://drone.fpfis.eu/ec-europa/europaeu-reference
* **Deployments**: https://ec.deploy.fpfis.eu/ec-europ/ec-europa/europaeu-reference


## Contacts

This section is provided by composer.json which can list all active contacts (authors) for the project. Allowing project managers to edit this file without having knowledge about git throug f.e. a REST interface can help us provide all listed contacts with automatic access based on the defined role to allow them to access resources and links related to the project AFTER the change request to the code is approved.

* **Lead developer**: Santos Joao - santos.joao@example.com
* **Developer**: Iulian Mamaliga - iulian.mamaliga@example.com
* **Webmaster**: Alexander Verbruggen - alexander.verbruggen@example.com
* **Project owner**: Florin Bota - florin.bota@example.com

## Support

This section is provided by composer.json and can list most of the links that people need to be able to work on the project. Any time a project switches maintainers or repository provider they have all information required to pick up where they left from the moment they clone the repository.

* **First Level Support**: send an email to europamanagement@ec.europa.eu
* **Documentation**: https://verbruggenalex.github.io/example-project/
* **Wiki Page**: [https://webgate.ec.europa.eu/fpfis/wikis/pages/project-page](https://webgate.ec.europa.eu/fpfis/wikis/pages/viewpage.action?spaceKey=MULTISITE&title=Projects)
* **Issue Queue**: https://github.com/verbruggenalex/example-project/issues
* **Guidelines**: [https://webgate.ec.europa.eu/fpfis/wikis/pages/guide-into-code-reviewing-for-drupal-7](https://webgate.ec.europa.eu/fpfis/wikis/pages/viewpage.action?spaceKey=MULTISITE&title=Guide+into+code+reviewing+for+Drupal+7)
* **Team chat**: https://github.com/ekmartin/slack-irc
