#TimeMachine

Исключение данных TimeMachine для исключения из бекапа данных которые изначально не надо-бы копировать, к примеру кэши и логи, tmp и тд.

Также в список добавляются большие ресурсные пакеты которые должны быть загружены снаружи. К примеру симуляторы для Xcode.

Список составлен мной и для меня так-что если что я не виноват.

## CLI для машинного исключения

Tmutil command allows you to query, set, and delete file exclusions from the command line:

`tmutil isexcluded _item_` will determine if the volume, directory or file is currently excluded.
`tmutil addexclusion _item_` sets an exclusion rule so that the item (even if moved to a new location or renamed) will be excluded from future backups.
`tmutil addexclusion -p _item_` устанавливает правило исключения таким образом, чтобы путь к элементу был исключен. Это остается неизменным, поэтому при перемещении файла его резервная копия будет создана, если не по этому точному пути, а также предотвратит резервное копирование файла, если он вернется в то же расположение, которое указано в правиле.
`tmutil removeexclusion _item_` removed either type of exclusion rule as appropriate.

Список от меня:
```bash
tmutil addexclusion ~/Library/Developer/CoreSimulator && \
tmutil addexclusion ~/Library/Developer/Xcode/DerivedData && \
tmutil addexclusion '~/Library/Developer/Xcode/watchOS DeviceSupport' && \
tmutil addexclusion ~/Library/Developer/Xcode/Products
tmutil addexclusion ~/Movies/TV
tmutil addexclusion '~/Library/Application Support/com.robotsandpencils.XcodesApp'
```
Под вопросом, возможно установлено системой по умолчанию:
```bash
tmutil addexclusion /private/var/log
tmutil addexclusion ~/Library/Cashes && \
tmutil addexclusion ~/Library/Logs && \
```