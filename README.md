# issue-triage

> Cada issue en un estado, y los listos con un brief ejecutable.

**Triage de issues** · Skill para agentes de código de la comunidad [nvvdev](https://github.com/nvv-dev). Funciona en Claude Code como plugin o como skill suelta, y en cualquier agente compatible con el formato abierto [`SKILL.md`](https://agentskills.io).

*English summary at the end.*

## Qué hace

Clasifica issues o ideas en cinco estados (por revisar, necesita información, listo para agente, listo para humano, no se hará), detecta duplicados, pide la información que falta y escribe un brief autocontenido para los que un agente puede tomar.

## Objetivo

Un backlog que se puede delegar sin explicar el contexto cada vez.

## Cuándo usarla

- Ordenar un backlog o un lote de reportes
- Preparar trabajo para agentes

## Cuándo no

- Un solo issue ya claro

## Ejemplo

```text
Haz triage de los issues abiertos con la etiqueta bug.
```

## Cómo se activa

Esta skill **se activa sola**: Claude Code lee su descripción y la carga cuando la tarea coincide. También puedes pedirla por nombre ("usa la skill issue-triage") o invocarla con `/issue-triage:issue-triage` (plugin) o `/issue-triage` (copiada a `.claude/skills/`).

## Instalación

### Opción 1: Claude Code, como plugin (recomendada)

Dentro de Claude Code:

```text
/plugin marketplace add nvv-dev/claude-plugins
/plugin install issue-triage@nvvdev
```

La primera línea agrega el catálogo de nvvdev una sola vez; la segunda instala esta skill. Si prefieres el paquete completo, instala `dev-workflow@nvvdev` en su lugar (incluye esta skill y las demás de [dev-workflow](https://github.com/nvv-dev/dev-workflow)); no instales los dos a la vez.

### Opción 2: Claude Code, copiando la skill

Para un solo proyecto (se comparte con tu equipo por git):

```bash
git clone --depth 1 https://github.com/nvv-dev/issue-triage.git /tmp/issue-triage
mkdir -p .claude/skills
cp -R /tmp/issue-triage/skills/issue-triage .claude/skills/
```

Para todos tus proyectos, cópiala en `~/.claude/skills/` en lugar de `.claude/skills/`.

### Opción 3: otros agentes

Copia la carpeta `skills/issue-triage/` en la carpeta de skills de tu agente (cada agente documenta la suya). Con la CLI [skills](https://github.com/vercel-labs/skills) de Vercel Labs:

```bash
DISABLE_TELEMETRY=1 npx skills add nvv-dev/issue-triage
```

### Verificar

Abre una sesión nueva y pregunta "¿qué skills tienes disponibles?"; `issue-triage` debe aparecer. Con el plugin, `/plugin` la muestra como instalada.

### Actualizar o desinstalar

- Plugin: `/plugin marketplace update nvvdev` para actualizar; `/plugin uninstall issue-triage@nvvdev` para quitarla.
- Copia manual: repite la copia para actualizar, o borra la carpeta `.claude/skills/issue-triage`.

Antes de instalar cualquier skill, incluida esta, conviene leerla: es un solo archivo, [`skills/issue-triage/SKILL.md`](skills/issue-triage/SKILL.md). Ver [vetting-external-skills](https://github.com/nvv-dev/vetting-external-skills).

## Contenido

| Ruta | Qué es |
|---|---|
| `skills/issue-triage/SKILL.md` | La skill: instrucciones en inglés para que los escáneres de seguridad las analicen completas; el agente responde en tu idioma |
| `.claude-plugin/plugin.json` | Manifiesto para instalarla como plugin |
| `.github/workflows/` | Validación de estructura y escaneo con SkillSpector en cada cambio |

## Contribuir

Este repo se **genera** desde [nvv-dev/dev-workflow](https://github.com/nvv-dev/dev-workflow), donde vive la versión canónica. Abre issues y PRs allí. La mejor contribución es un caso real en la sección *Known failures* de la skill, con la regla que lo evita.

## Origen

Escrita desde cero por nvvdev. Inspirada en: [mattpocock/skills](https://github.com/mattpocock/skills) (triage).

## Licencia

MIT.

---

## English

**issue-triage** — Assigns each item one of five states and writes self-contained briefs for agent-ready work.

Install in Claude Code with `/plugin marketplace add nvv-dev/claude-plugins` and `/plugin install issue-triage@nvvdev`, or copy `skills/issue-triage/` into `.claude/skills/` (project) or `~/.claude/skills/` (personal). Other agents: copy the folder into their skills directory, or run `DISABLE_TELEMETRY=1 npx skills add nvv-dev/issue-triage`. Loads automatically when the task matches its description. Canonical source: [nvv-dev/dev-workflow](https://github.com/nvv-dev/dev-workflow). License: MIT.
